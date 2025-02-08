////////////////////
public function update_warganegara()
//public function kirim($mahasiswa_kode)
	{
	    //Token_uwm_model_dev
		set_time_limit(0);
        $token = $this->tkn_dev->token_simak(); 
		
		$manual = array();
		//LIST DARI DATA//
//		$this->db->where(
//		       array('tahun_masuk'=> $tahun_angkatan,
 
//		      )
//		     );
		 $query = $this->db->get('un_mahasiswa'); 	

		//$this->db->where(
		  //      array('mahasiswa_kode'=> $mahasiswa_kode,
		    ///    'un_mahasiswa_id'=> '')
		       // );
		        //$query = $this->db->get('un_mahasiswa'); 	
		if( $query->num_rows() > 0) 
		{
			$result = $query->result(); //or $query->result_array() to get an array
			foreach( $result as $rows )
			{									
				$manual = 
				    array(
				        
				        'token'=>$token,
                        'un_mahasiswa_id' => $rows->un_mahasiswa_id_dev,				        				        
                        'flag_wna' => $rows->flag_wna,				        
                        'dana_administrasi_wna' => $rows->dana_administrasi_wna,
                            				        );
            				/////////////////// DATA JSON YANG DIKIRIM //////////////	
            				echo '>';
            				echo " " . json_encode($manual,true);
            				$data_manual = json_encode($manual,true);
				/////////////////////////////////////////////////////////
				//echo $data_manual;
						/////CURL///////////////////////////////////////
						///$this->load->library('Curl');	
						///developer
						$url = 'http://202.162.33.122:10001/un_mahasiswa/update';						
						//$url = 'https://api.widyamataram.ac.id/un_mahasiswa/insert';
						$this->curl->create($url);
						$this->curl->option(CURLOPT_HTTPHEADER, array('Content-Type: application/json','Content-Length: ' . strlen($data_manual)));
						$this->curl->post($data_manual);
						$result_profil = $this->curl->execute();
						///////////////////////////////////////////////
						
							//////RESPON///// 
							$coba = json_decode($result_profil);
							$data_sync = json_encode($coba->kode,true);
							
							echo 'dataku ini '.$data_sync;
							
 							$data_response1 = json_encode($coba);
							//$data_response2 = json_encode($coba->data);
							
							echo 'response ini '. $data_response1;
							//echo $data_response2;
							////////////////

								///MENGELOLARESPON///
								if ($data_sync == '200')
										{

                                    echo "OK";												
												
										} 
								else if ($data_sync == '1')
										{
											echo "Gagal";
										}
								////////////////////////////
			}
			/////////////////////
			$this->curl->close();
			//CLOSE CURL seperti curl_close($ch);///				
			/////////////////////
		}	
 } 
///////////////////////////
///////////////////////////
