## CrystalReportsApi

There is only one method here **`api/report`**.   

This method accepts an xml file with data and options (the same file that can be
supplied to ReportDaemon) and generates and returns a pdf document.
When a `clientId` is supplied, the document is also sent to blob storage 
(for the client to print). 

It is a REST POST api that only accepts 'multipart/form-data' content. 
A request can contain multiple files, but needs at least one xml file.
It can also contain a "ClientId" parameter (necessary when you want the document 
to be printed somewhere).
The service will also return the generated document. 

In the case of multiple documents in the xml, only the first one will be returned, 
but all of them will be sent to blob storage (of course only when `clientId` is supplied).

An example call looks like this:

    POST http://serverlessprintingdev.westeurope.azurecontainer.io/api/report HTTP/1.1
    Host: serverlessprintingdev.westeurope.azurecontainer.io
    Connection: keep-alive
    Content-Length: 22863
    Cache-Control: max-age=0
    Origin: http://serverlessprintingdev.westeurope.azurecontainer.io
    Upgrade-Insecure-Requests: 1
    DNT: 1
    Content-Type: multipart/form-data; boundary=----WebKitFormBoundarybll3CwuoiJ1pQBTZ
    User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.128 Safari/537.36 Edg/89.0.774.77
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
    Referer: http://serverlessprintingdev.westeurope.azurecontainer.io/
    Accept-Encoding: gzip, deflate
    Accept-Language: nl-BE,nl;q=0.9,en;q=0.8
    sec-gpc: 1
    
    ------WebKitFormBoundarybll3CwuoiJ1pQBTZ
    Content-Disposition: form-data; filename="XPOWER-HD-INV.xml"
    Content-Type: text/xml
    
    <?xml version="1.0" encoding="ISO-8859-1" ?><lijst type="invoice"> <doc><specs><LayoutBak>Tray 2</LayoutBak><LayoutExamp>0</LayoutExamp><LayoutPrinter>XPWBELHQADMPRT01</LayoutPrinter><Layout>C:\xml\rpt\XPOWER-HD-INV</Layout><Aantal>1</Aantal><ServiceAction>p</ServiceAction><Batchverwerkingmode>P</Batchverwerkingmode><pdfName>210326112520-220120521_IN1_29.pdf</pdfName><pdfDirectory>C:\Users\LIEVEN~1.VAN\AppData\Local\Temp\</pdfDirectory><pdfExport>yes</pdfExport><mail_address_to_list>serwis@manzerniki.pl</mail_address_to_list><mail_subject>Proforma 220120521</mail_subject><mail_body>Dear customer,&lt;br /&gt;&lt;br /&gt;In attachment you can find our invoice for delivered products or services from Xpower NV. You will only receive this invoice digitally, it will not be sent by regular mail.&lt;br /&gt;&lt;br /&gt;If you have any questions about this invoice, please contact our administration by email: finance@xpower.be or by phone: +3293539020&lt;br /&gt;&lt;br /&gt;Kind regards,&lt;br /&gt;&lt;br /&gt;Xpower NV&lt;br /&gt;Toleindestraat 7/0101&lt;br /&gt;9080 Beervelde</mail_body><EmailConfiguratie><EmailBijlagen><Bijlage>c:\xpower\rpt\GeneralConditions.pdf</Bijlage></EmailBijlagen></EmailConfiguratie><diasxml/></specs><pr-set><pr><NRrec>0x00000000026dc684</NRrec><NRpr>220120521</NRpr><CDrel>K</CDrel><NRrel>104471</NRrel><CDpr>2</CDpr><NRown>220120521</NRown><NRproject>MANPL</NRproject><CNcn>0</CNcn><CNcn-inv>0</CNcn-inv><CDstatus>0</CDstatus><DAin>14/12/2020</DAin><TMin>0000</TMin><DAout>24/03/2021</DAout><TMout>0000</TMout><DAout-promised> </DAout-promised><TMout-promised>0000</TMout-promised><CNtime-plan>0</CNtime-plan><NRpart>0</NRpart><NRwh>1</NRwh><DAcreate>14/12/2020</DAcreate><UScreate>Kathy</UScreate><YNwait>No </YNwait><NMref></NMref><NRvendor>Dieth</NRvendor><NRtech></NRtech><NRcontact>0</NRcontact><NRlicpl></NRlicpl><NRcust-src>0</NRcust-src><NRarchive></NRarchive><YNmain>No </YNmain><YNSequel>No </YNSequel><YNrepeat-repair>No </YNrepeat-repair><NRinfo>0</NRinfo><YNbo>Yes</YNbo><NRcust-owner>104471</NRcust-owner><CDfollow-up></CDfollow-up><INfollow-up></INfollow-up><CDresult></CDresult><INresult></INresult><USresult>Kathy</USresult><DTresult>14/12/2020 15:55:01,368</DTresult><CDnotify></CDnotify><INnotify></INnotify><DAcall> </DAcall><CDcall></CDcall><TMcall></TMcall><UScall></UScall><INcall></INcall><PRbudget>0,00</PRbudget><CDic>F</CDic><INtitle>Proforma 220120521</INtitle><INpr>CONSULTANCY APPLICATION</INpr><NMvendor>Diether Reyntjens</NMvendor><NMtech /><CDlang-print>E</CDlang-print><USprint>Lieven</USprint><NMprint>Lieven Van Hecke</NMprint><NMwh>XPOWER Beervelde</NMwh><NMproject>MAN POLAND</NMproject><INruntime1>1F</INruntime1><INruntime2 /><INruntime3 /><INruntime4 /><INruntime5 /><INruntime6 /><INruntime7 /><INruntime8 /><INfoot1 /><INfoot2 /><INfoot3 /><INfoot4 /><INfoot5 /><INhead1 /><INhead2 /><INhead3 /><INhead4 /><INhead5 /><DTmach-in /><DTmach-out /><DTexec /><CDpay-method /><NMpay-method /><CDaction-print /></pr></pr-set><pr_ln-set><pr_ln><NRrec>0x0000000002ba7fc7</NRrec><NRpr>220120521</NRpr><NRsub>2</NRsub><NRjob>0</NRjob><NRln>1</NRln><NRln-id>12002</NRln-id><CDass>1</CDass><CDstatus /><YNinv>yes</YNinv><CDprnt /><CDrel>D</CDrel><NRrel>VRS</NRrel><INln>30% Advance O5421</INln><INln-x1 /><INln-x2 /><INln-x3 /><INln-x4 /><NRbrnd>0</NRbrnd><NRwh>1</NRwh><PRout>       6000,0000</PRout><PRtot>       6000,00</PRtot><PRtot-i>          0,00</PRtot-i><CNneed>          1,00</CNneed><CNext>          0,00</CNext><WGln>         0,000</WGln><CDintra /><CDcnty-orig /><CDdisc /><PCdisc>   0,00</PCdisc><NMdisc /><PCext> 100,00</PCext><NRref-cust /><NRser /><NMcall-prt-ser /><CDinv /><INinv /><INinv-extern /><NMpkg /><CDit /><CDvat>  5</CDvat><PCvat>   0,00</PCvat><NRprod> 0</NRprod><CDprod>VRS</CDprod><DAcreate>24/03/2021</DAcreate><UScreate>Kathy</UScreate><USln>20210324 Kathy</USln><NRinfo>0</NRinfo><NRprt-cust /><INprt-cust /><CDopt-prt-cust /><CDstatus-prt-cust /><INln2 /><CDtask /><INtask /><CDsrc /><DAneed /><YNurgent>no </YNurgent><NRpr-con>00000000</NRpr-con><NRsub-con>01</NRsub-con><NRpr-rel /><CNwork /><PRnet1>       6000,0000</PRnet1><PRbrut-tot>       6000,0000</PRbrut-tot><PRnet-tot>       6000,0000</PRnet-tot><PRnet-i>          0,0000</PRnet-i><PRnet-tot-i>          0,0000</PRnet-tot-i><PRincl>       6000,00</PRincl><NMbrnd /><CDunit-opr /><NMprt /><NRprt2 /><NRbarc-int /><INdim /><CNweight /><CDsort>00001</CDsort><YNclaim>no </YNclaim><NRbarcode /><NRbarc-b9 /><CNwar>         0</CNwar><INxtra /><NRplace /><CNstock>0</CNstock><PReu>          0,0000</PReu><CDinv-type>E</CDinv-type><YNok>no </YNok><YNexceptional>no </YNexceptional><NRprt-eq /></pr_ln></pr_ln-set><pr_inv-set><pr_inv><NRrec>0x0000000002ba7fc5</NRrec><NRpr>220120521</NRpr><CDass>1</CDass><NRfy>221</NRfy><NRjrnl>C5</NRjrnl><NRinv>500001</NRinv><NRcust>104471</NRcust><CDlang-inv>2</CDlang-inv><DAinv>24/03/2021</DAinv><DAexpire>23/04/2021</DAexpire><CDinv></CDinv><CDstatus-inv>9</CDstatus-inv><NRfy-int>?</NRfy-int><NRjrnl-int>?</NRjrnl-int><NRdiv>?</NRdiv><CDpaycon>30</CDpaycon><YNfoot>Yes</YNfoot><PCfin-disc>0,00</PCfin-disc><VAfin-disc>0,00</VAfin-disc><PCadd-on>0,00</PCadd-on><PRadd-on>0,00</PRadd-on><NRinv-version>0</NRinv-version><CDcurr>EUR</CDcurr><CNrate>1,0000</CNrate><CNrateday>1,0000</CNrateday><PRtot-i>0,00</PRtot-i><PRtot-claim>0,00</PRtot-claim><CDintra-load></CDintra-load><CDtransp></CDtransp><CDtransact></CDtransact><NRcontact>0</NRcontact><CDdep></CDdep><CDcnd-intra></CDcnd-intra><NRinfo>0</NRinfo><INref></INref><UScreate-inv>Kathy</UScreate-inv><DAinv-print>25/03/2021</DAinv-print><NRinv-version>0</NRinv-version><WGpr-inv>         0,000</WGpr-inv><NRinv-ext>221.C5.500001</NRinv-ext><NRinv-int /><PRout>       6000,00</PRout><PRvat>          0,00</PRvat><PRincl>       6000,00</PRincl><PRall>       6000,00</PRall><PRall-vat>          0,00</PRall-vat><PRall-incl>       6000,00</PRall-incl><PRtot-work>          0,00</PRtot-work><CNtot-work>          0,00</CNtot-work><PRincl-letter>2384 xmsg language -> 2 ?</PRincl-letter><PRbrut>       6000,00</PRbrut><PRbrut-vat>          0,00</PRbrut-vat><PRbrut-incl>       6000,00</PRbrut-incl><PRdisc>          0,00</PRdisc><PRout-bo>          0,00</PRout-bo><PRvat-bo>          0,00</PRvat-bo><PRincl-bo>          0,00</PRincl-bo><Name-adress-ln1>TRUCK EURO SERVICE &quot;WIELKOPOLSKA&quot; SP. Z O.O.</Name-adress-ln1><Name-adress-ln2>ul. Jana Gutenberga 2, Zerniki</Name-adress-ln2><Name-adress-ln3>62-035 Kornik</Name-adress-ln3><Name-adress-ln4>POLAND</Name-adress-ln4><Name-adress-ln5 /><Name-adress-ln6 /><Name-adress-ln7 /><NMpaycon /><NRstruct>104/4710/00119</NRstruct><NRdos-ext /></pr_inv></pr_inv-set><pr_sub-set><pr_sub><NRrec>0x0000000002ba7fc6</NRrec><NRpr>220120521</NRpr><NRsub>2</NRsub><NRcust>104471</NRcust><CDloc></CDloc><CDass>1</CDass><NRdlv></NRdlv><DAsub>24/03/2021</DAsub><TMsub></TMsub><CDstatus>9</CDstatus><INref></INref><INsub></INsub><INpay-method></INpay-method><NMreceiver></NMreceiver><DAcreate>24/03/2021</DAcreate><UScreate>Kathy</UScreate><VAfin-disc>0,00</VAfin-disc><PCfin-disc>0,00</PCfin-disc><CDtransprt></CDtransprt><CDcnd-transprt></CDcnd-transprt><NRtransprt>0</NRtransprt><INtransprt></INtransprt><DAdlv> </DAdlv><TMdlv></TMdlv><NRwh></NRwh><NRcontact>0</NRcontact><CNcolli>0,00</CNcolli><CNvol>0,0000</CNvol><WGsub>0,0000</WGsub><NRvendor></NRvendor><NRtech></NRtech><CDpr-org></CDpr-org><NRown-org></NRown-org><NRsub-org>0</NRsub-org><NRinfo>0</NRinfo><DAin> </DAin><TMin>0000</TMin><DAout> </DAout><TMout>0000</TMout><CDrepair></CDrepair><DAprint> </DAprint><USprint></USprint><NRdoc-fisc></NRdoc-fisc><DTdoc-fisc></DTdoc-fisc><USdoc-fisc></USdoc-fisc><INdoc-fisc></INdoc-fisc><CDdoc-fics></CDdoc-fics><NRdoc-trans></NRdoc-trans><DTdoc-trans></DTdoc-trans><USdoc-trans></USdoc-trans><INdoc-trans></INdoc-trans><CDdoc-trans></CDdoc-trans><INtransport-reason></INtransport-reason><WGpr-sub>         0,000</WGpr-sub><NMvendor>ALGEMEEN</NMvendor><NMtech /><NRpr-time>2012052102</NRpr-time><NMcie /><INcnd-transprt /><PRout>       6000,00</PRout><PRtot-work>          0,00</PRtot-work><CNtot-work>          0,00</CNtot-work><Name-adress-ln1>TRUCK EURO SERVICE &quot;WIELKOPOLSKA&quot; SP. Z O.O.</Name-adress-ln1><Name-adress-ln2>ul. Jana Gutenberga 2, Zerniki</Name-adress-ln2><Name-adress-ln3>62-035 Kornik</Name-adress-ln3><Name-adress-ln4>POLAND</Name-adress-ln4><Name-adress-ln5 /><Name-adress-ln6 /><Name-adress-ln7 /><DAtime-first /><DAtime-last /><CNdim1>0</CNdim1><CNdim2>0</CNdim2><CNdim3>0</CNdim3><NRmach /><CDrel>K</CDrel><NRrel>104471</NRrel></pr_sub></pr_sub-set><vat-set><vat><NRpr>220120521</NRpr><CDass>1</CDass><CDvat>  5</CDvat><PCvat>   0,00</PCvat><PRout>       6000,00</PRout></vat></vat-set><pr_pay-set></pr_pay-set><intra-set></intra-set><vat_txt-set><vat_txt><CDvat>5</CDvat><CDtxt>cdvat-05</CDtxt><NRln>10</NRln><INtxt>&quot;VAT Reverse Charge&quot;</INtxt></vat_txt></vat_txt-set><pkg_ln-set></pkg_ln-set><pr_task-set></pr_task-set><pr_comm-set></pr_comm-set><pr_contact-set></pr_contact-set><rnt-set></rnt-set><rntobj-set></rntobj-set><pr_rel-set></pr_rel-set><mach-set></mach-set><loc-set></loc-set><ric-set></ric-set><cust-set><cust><NRcust>104471</NRcust><NRrec>0x0000000001649fd3</NRrec><CDcust>05</CDcust><CDcust-disc></CDcust-disc><NMcall>TRUCKEURO</NMcall><NMcust>TRUCK EURO SERVICE</NMcust><NMcust2>&quot;WIELKOPOLSKA&quot; SP. Z O.O.</NMcust2><NMcontact></NMcontact><TIcust></TIcust><TIcomm></TIcomm><NMini></NMini><ADcust>ul. Jana Gutenberga 2, Zerniki</ADcust><ADcust2></ADcust2><NRhouse></NRhouse><NRbox></NRbox><CIcust>Kornik</CIcust><NRzip>62-035</NRzip><CDcnty>PL</CDcnty><CDdistri></CDdistri><NRtel>+48612224688</NRtel><NRtel2></NRtel2><NRtel-mob></NRtel-mob><NRtel-mob2></NRtel-mob2><NRfax>+ 48 61 62 62 281</NRfax><ADemail>serwis@manzerniki.pl</ADemail><CDlang>2</CDlang><NRvat>PL7822045009</NRvat><NRdomicil></NRdomicil><INcust></INcust><CDstatus></CDstatus><NRfleet></NRfleet><YNprof>No </YNprof><CDstic>K--------</CDstic><NRvendor>Dieth</NRvendor><NMfam>MAN</NMfam><NRdom></NRdom><ADurl-1></ADurl-1><ADurl-2></ADurl-2><ADurl-3></ADurl-3><NRcust-ext></NRcust-ext><NRproject></NRproject><NRarchive></NRarchive><NRnational></NRnational><NRcommerce></NRcommerce><NRinfo>0</NRinfo><NRaccx-1></NRaccx-1><NRaccx-2></NRaccx-2><NRaccx-3></NRaccx-3><NRaccx-4></NRaccx-4><NRaccx-5></NRaccx-5><NMaccx-1></NMaccx-1><NMaccx-2></NMaccx-2><NMaccx-3></NMaccx-3><NMaccx-4></NMaccx-4><NMaccx-5></NMaccx-5><CDaccx-1></CDaccx-1><CDaccx-2></CDaccx-2><CDaccx-3></CDaccx-3><CDaccx-4></CDaccx-4><CDaccx-5></CDaccx-5><INaccx-1></INaccx-1><INaccx-2></INaccx-2><INaccx-3></INaccx-3><INaccx-4></INaccx-4><INaccx-5></INaccx-5><CDsrc></CDsrc><NRinv-version>0</NRinv-version><YNskip-mail>No </YNskip-mail><CDpaycon>30</CDpaycon><CDpay-frn></CDpay-frn><ADemail2></ADemail2><NMcnty>POLAND</NMcnty><NRzip2 /><NMprovince /><NMdistrict /><INtype>POLEN</INtype><PCvat-default>   0,00</PCvat-default></cust><cust><NRcust>0</NRcust><NRrec>0x00000000009cf5c1</NRrec><CDcust>00</CDcust><CDcust-disc></CDcust-disc><NMcall>PRT</NMcall><NMcust>XPOWER nv/sa</NMcust><NMcust2></NMcust2><NMcontact></NMcontact><TIcust>N.V.</TIcust><TIcomm></TIcomm><NMini></NMini><ADcust>Toleindestraat 7/0101</ADcust><ADcust2></ADcust2><NRhouse></NRhouse><NRbox></NRbox><CIcust>BEERVELDE</CIcust><NRzip>BE-9080</NRzip><CDcnty>BE</CDcnty><CDdistri></CDdistri><NRtel>+32 (0)9 353 90 20</NRtel><NRtel2></NRtel2><NRtel-mob></NRtel-mob><NRtel-mob2></NRtel-mob2><NRfax>+32 (0)9 353 90 29</NRfax><ADemail>contact@xpower.be</ADemail><CDlang></CDlang><NRvat>BE0451526090</NRvat><NRdomicil></NRdomicil><INcust></INcust><CDstatus>H</CDstatus><NRfleet></NRfleet><YNprof>No </YNprof><CDstic>1--------</CDstic><NRvendor></NRvendor><NMfam></NMfam><NRdom></NRdom><ADurl-1>www.xpower.be</ADurl-1><ADurl-2></ADurl-2><ADurl-3></ADurl-3><NRcust-ext></NRcust-ext><NRproject></NRproject><NRarchive></NRarchive><NRnational></NRnational><NRcommerce>test</NRcommerce><NRinfo>0</NRinfo><NRaccx-1>BE74 3900 5222 9707</NRaccx-1><NRaccx-2>BE49 0689 0900 1171</NRaccx-2><NRaccx-3></NRaccx-3><NRaccx-4></NRaccx-4><NRaccx-5></NRaccx-5><NMaccx-1>ING</NMaccx-1><NMaccx-2>BELFIUS</NMaccx-2><NMaccx-3></NMaccx-3><NMaccx-4></NMaccx-4><NMaccx-5></NMaccx-5><CDaccx-1>BBRUBEBB</CDaccx-1><CDaccx-2>GKCCBEBB</CDaccx-2><CDaccx-3></CDaccx-3><CDaccx-4></CDaccx-4><CDaccx-5></CDaccx-5><INaccx-1></INaccx-1><INaccx-2></INaccx-2><INaccx-3></INaccx-3><INaccx-4></INaccx-4><INaccx-5></INaccx-5><CDsrc></CDsrc><NRinv-version>0</NRinv-version><YNskip-mail>No </YNskip-mail><CDpaycon>30</CDpaycon><CDpay-frn>60</CDpay-frn><ADemail2></ADemail2><NMcnty>BELGIUM</NMcnty><NRzip2 /><NMprovince /><NMdistrict /><INtype>BELGI </INtype><PCvat-default>  21,00</PCvat-default></cust></cust-set><rel_contact-set></rel_contact-set><mach_sell-set></mach_sell-set><user-set><user><NRrec>0x000000000021a20d</NRrec><USuserparm>Kathy</USuserparm><NMuserparm>Kathy De Groote</NMuserparm><ADuserparm></ADuserparm><CIuserparm></CIuserparm><NMjob>Admin./Boek.</NMjob><NRtel-priv></NRtel-priv><NRtel></NRtel><NRfax></NRfax><NRgsm></NRgsm><ADemail>kathy.degroote@xpower.be</ADemail><YNok-cost>Yes</YNok-cost><YNok-man>No </YNok-man><YNok-frn>Yes</YNok-frn><NRwh>1</NRwh><CDlang>F</CDlang></user><user><NRrec>0x0000000000166d1b</NRrec><USuserparm>lieven</USuserparm><NMuserparm>Lieven Van Hecke</NMuserparm><ADuserparm></ADuserparm><CIuserparm></CIuserparm><NMjob></NMjob><NRtel-priv></NRtel-priv><NRtel></NRtel><NRfax></NRfax><NRgsm></NRgsm><ADemail>lieven.vanhecke@xpower.be</ADemail><YNok-cost>No </YNok-cost><YNok-man>No </YNok-man><YNok-frn>Yes</YNok-frn><NRwh>1</NRwh><CDlang>N</CDlang></user></user-set><fld_lbl-set><fld_lbl><CDrel>K</CDrel><NRrel>*</NRrel><NRfld>124</NRfld><INlbl>FACTURATIE</INlbl></fld_lbl><fld_lbl><CDrel>K</CDrel><NRrel>*</NRrel><NRfld>101</NRfld><INlbl>BOEKHOUDING</INlbl></fld_lbl><fld_lbl><CDrel>K</CDrel><NRrel>*</NRrel><NRfld>110</NRfld><INlbl>DOTSYS</INlbl></fld_lbl><fld_lbl><CDrel>K</CDrel><NRrel>*</NRrel><NRfld>111</NRfld><INlbl>PROGRESS</INlbl></fld_lbl><fld_lbl><CDrel>K</CDrel><NRrel>*</NRrel><NRfld>122</NRfld><INlbl>PROGRESSVERVALDATUMLICENTIE</INlbl></fld_lbl><fld_lbl><CDrel>K</CDrel><NRrel>*</NRrel><NRfld>123</NRfld><INlbl>OPSTARTDATUM</INlbl></fld_lbl><fld_lbl><CDrel>K</CDrel><NRrel>*</NRrel><NRfld>125</NRfld><INlbl>AZURE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>34</NRfld><INlbl>XPOWERVERSIE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>35</NRfld><INlbl>XPOWERUSERS</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>36</NRfld><INlbl>XPOWERANDERE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>37</NRfld><INlbl>PROGR.1VERSIE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>38</NRfld><INlbl>PROGR.1OMSCHR</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>39</NRfld><INlbl>PROGR.1SERIAL</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>40</NRfld><INlbl>PROGR.1KEY</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>42</NRfld><INlbl>PROGR.1USERS</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>41</NRfld><INlbl>PROGR.2VERSIE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>43</NRfld><INlbl>PROGR.2OMSCHR</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>44</NRfld><INlbl>PROGR.2SERIAL</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>45</NRfld><INlbl>PROGR.2KEY</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>46</NRfld><INlbl>PROGR.2USERS</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>47</NRfld><INlbl>PROGR.3VERSIE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>48</NRfld><INlbl>PROGR.3OMSCHR</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>49</NRfld><INlbl>PROGR.3SERIAL</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>50</NRfld><INlbl>PROGR.3KEY</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>51</NRfld><INlbl>PROGR.3USERS</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>52</NRfld><INlbl>XPONENTVERSIE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>53</NRfld><INlbl>XPONENTSERIAL</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>54</NRfld><INlbl>XPONENTID-KEY</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>55</NRfld><INlbl>XPONENTUSERS</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>66</NRfld><INlbl>FUSION95VERS.</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>56</NRfld><INlbl>FUSION95USERS</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>57</NRfld><INlbl>FUSION95KEY1</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>58</NRfld><INlbl>FUSION95KEY2</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>59</NRfld><INlbl>FUSION95KEY3</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>60</NRfld><INlbl>FUSION95KEY4</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>61</NRfld><INlbl>FUSION95KEY5</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>62</NRfld><INlbl>FUSION95KEY6</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>63</NRfld><INlbl>FUSION95KEY7</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>64</NRfld><INlbl>FUSION95KEY8</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>65</NRfld><INlbl>FUSION95KEY9</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>83</NRfld><INlbl>FUSION95KEY10</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>84</NRfld><INlbl>FUSION95KEY11</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>85</NRfld><INlbl>FUSION95KEY12</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>86</NRfld><INlbl>FUSION95KEY13</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>67</NRfld><INlbl>UNIXVERSIE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>68</NRfld><INlbl>UNIXLIC-NR</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>69</NRfld><INlbl>UNIXLIC-CODE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>70</NRfld><INlbl>UNIXLIC-DATA</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>71</NRfld><INlbl>UNIXUSERSTOT</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>72</NRfld><INlbl>UNIXLIC2-NR</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>73</NRfld><INlbl>UNIXLIC2-CODE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>74</NRfld><INlbl>UNIXLIC2-DATA</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>29</NRfld><INlbl>VICKING</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>87</NRfld><INlbl>PSION</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>88</NRfld><INlbl>ROUTER</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>75</NRfld><INlbl>SERVERCPU</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>76</NRfld><INlbl>SERVERRAM</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>77</NRfld><INlbl>SERVERH-DISK</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>79</NRfld><INlbl>SERVERSERIAL</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>78</NRfld><INlbl>SERVERTYPE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>80</NRfld><INlbl>SERVERTAPE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>81</NRfld><INlbl>SERVERCD</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>20</NRfld><INlbl>CONTROLLER</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>23</NRfld><INlbl>NIC</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>14</NRfld><INlbl>MAINTENANCE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>13</NRfld><INlbl>INSTALLATIE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>12</NRfld><INlbl>LAATSTEUPDATE</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>2</NRfld><INlbl>SOURCES</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>3</NRfld><INlbl>OBJECTS</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>4</NRfld><INlbl>DATABASES</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>5</NRfld><INlbl>SCRIPTS</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>32</NRfld><INlbl>LAN-PATH</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>31</NRfld><INlbl>ADMINUSER</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>28</NRfld><INlbl>P</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>30</NRfld><INlbl>MODEMSUPPORT</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>82</NRfld><INlbl>MODEMTEL-NR</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>1</NRfld><INlbl>VERSIEXPOWER</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>33</NRfld><INlbl>XPOWERUSERS</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>9</NRfld><INlbl>VERSIEXPONENT</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>10</NRfld><INlbl>VERSIEPROGRES</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>11</NRfld><INlbl>VERSIEUNIX</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>15</NRfld><INlbl>VERSIENETWERK</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>6</NRfld><INlbl>XPOWERUSERS</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>7</NRfld><INlbl>XPONENTUSERS</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>8</NRfld><INlbl>PROGRESSUSERS</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>*</NRrel><NRfld>16</NRfld><INlbl>NETWERKUSERS</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>DB</NRrel><NRfld>118</NRfld><INlbl>VPNType</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>DB</NRrel><NRfld>114</NRfld><INlbl>InternIPadres</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>DB</NRrel><NRfld>115</NRfld><INlbl>ExternIPadres</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>DB</NRrel><NRfld>117</NRfld><INlbl>SSLExtern</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>DB</NRrel><NRfld>116</NRfld><INlbl>SSLIntern</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>DB</NRrel><NRfld>119</NRfld><INlbl>VPNName</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>DB</NRrel><NRfld>120</NRfld><INlbl>Used</INlbl></fld_lbl><fld_lbl><CDrel>W</CDrel><NRrel>DB</NRrel><NRfld>121</NRfld><INlbl>%used</INlbl></fld_lbl></fld_lbl-set><fld_data-set></fld_data-set><rem-set></rem-set><qr-set></qr-set></doc></lijst>
    ------WebKitFormBoundarybll3CwuoiJ1pQBTZ
    Content-Disposition: form-data; name="clientId"
    
    2f511562-490f-43ea-a6c4-f48df28e31a6
    ------WebKitFormBoundarybll3CwuoiJ1pQBTZ--

The "Accept-Language" header is important! 
It defines how the supplied xml will be parsed (important for numbers and dates).

### User Secrets
This project uses UserSecrets to manage the AzureStorageConnectionString appsetting.
For local development you have to add this setting to the secrets.xml file 
(right-click on project and select "Manage User Secrets"):

    <?xml version="1.0" encoding="utf-8"?>
    <root>
        <secrets ver="1.0">
            <secret name="AzureStorageConnectionString" value="your connectionstring" />
        </secrets>
    </root>

In a deployed container environment this setting needs to be set as an 
environment variable when starting the container.
