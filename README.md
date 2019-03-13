# firstgithub

                   $this->load->library('email');
                    $this->email->initialize(array(
                      'protocol' => 'smtp',
                      'smtp_host' => 'smtp.sendgrid.net',
                      'smtp_user' => 'myapikey',
                      'smtp_pass' => 'password',
                      'mailtype'=> 'text/html',
                      'smtp_port' => 587,
                      'crlf' => "\r\n",
                      'newline' => "\r\n"
                    ));
                    
                    
                    $mailcontent  = '';
                $mailcontent .= "<!doctype html>
                <html>
                <head>
                    <meta charset='utf-8'>
                </head>
                <body style='font-family:sans-serif;font-size:13px; line-height:22px;'>
                <div style='width: 100%;background:#f5f5f5;color: #000;'> 
                <div style='padding:30px 30px 60px 30px;'>       
                  <div style='text-align:center'><a href='" . base_url() . "'><img src='" . base_url() . "assets/admin/images/logo.png' style='margin:auto; margin-top:12px; margin-bottom:12px'></a>
                  </div>

                 <div style='background-color:#FFF;border:#EAEAEA 1px solid; padding:15px;'>
                    <p style='margin-top:30px;'>
                        
                        Event Id: $evntid <br></p>
                    
                    <div style='line-height:25px; margin-top:20px'>
                        <div>Sincerely,</div>
                        <div>ConferenceAlert.com</div>
                    </div>
                 </div>
                     
                  </div>        
                </div>

                </body>";
                
                
                 $from_mail = $this->Common_model->from_mail_id;    
                $this->email->set_header('MIME-Version', '1.0; charset=utf-8');
                $this->email->set_header('Content-type', 'text/html');
                $this->email->from($from_mail, "ConferenceAlert.com");
                $this->email->to($email);
                $this->email->cc($org_email);
                $this->email->subject($subject);
                $this->email->message($mailcontent);
                $this->email->send();
        
