---
title: "Mesajlaşma Protokolleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 600a1bd57015c6a64a51bf99f3ded35a375e62fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="messaging-protocols"></a>Mesajlaşma Protokolleri
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Kanal yığını iç ileti gösterimi kablo biçimine dönüştürme ve belirli bir kullanarak göndermek için kodlama ve taşıma kanalları kullanır. HTTP Web Hizmetleri birlikte çalışabilirlik için kullanılan en yaygın aktarım olduğunu ve Web Hizmetleri tarafından kullanılan en yaygın Kodlamalar XML tabanlı SOAP 1.1 ve SOAP 1.2 ileti iletim en iyi duruma getirme mekanizmasını (MTOM).  
  
 Bu konuda ele alınmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tarafından işe aşağıdaki protokolleri için uygulama ayrıntılarını <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.  
  
|Belirtim/belgesi|Bağlantı|  
|-----------------------------|----------|  
|HTTP 1.1|http://www.ietf.org/rfc/rfc2616.txt|  
|SOAP 1.1 HTTP bağlama|http://www.w3.org/TR/2000/Note-SOAP-20000508/, Bölüm 7|  
|SOAP 1.2 HTTP bağlama|http://www.w3.org/TR/soap12-part2/, Bölüm 7|  
  
 Bu konuda ele alınmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama ayrıntıları aşağıdaki protokoller için <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ve <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> kullanın.  
  
|Belirtim/belgesi|Bağlantı|  
|-----------------------------|----------|  
|XML|http://www.w3.org/TR/rec-XML|  
|SOAP 1.1|http://www.w3.org/TR/2000/Note-SOAP-20000508/|  
|SOAP 1.2 Çekirdek|http://www.w3.org/TR/soap12-part1/|  
|WS-adresleme 2004/08|http://www.w3.org/Submission/2004/SUBM-WS-Addressing-20040810/|  
|Adresleme 1.0 - çekirdek W3C Web Hizmetleri|http://www.w3.org/TR/2006/rec-ws-addr-Core-20060509|  
|Adresleme 1.0 - SOAP bağlama W3C Web Hizmetleri|http://www.w3.org/TR/2006/rec-ws-addr-SOAP-20060509|  
|Adresleme 1.0 - WSDL bağlama W3C Web Hizmetleri|http://www.w3.org/TR/2006/CR-ws-addr-WSDL-20060529/|  
W3C Web adresleme 1.0 - meta veri Hizmetleri|http://www.w3.org/TR/ws-addr-metadata/|  
|WSDL SOAP1.1 bağlama|http://www.w3.org/TR/WSDL/|  
|WSDL SOAP1.2 bağlama|http://www.w3.org/Submission/wsdl11soap12/|  
  
 Bu konuda ele alınmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama ayrıntıları aşağıdaki protokoller için <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> kullanır.  
  
|Belirtim/belgesi|Bağlantı|  
|-----------------------------|----------|  
|XOP|http://www.w3.org/TR/xop10/|  
|MTOM + SOAP 1.2 bağlama|http://www.w3.org/TR/soap12-MTOM/|  
|MTOM SOAP 1.1 bağlama|http://www.w3.org/Submission/soap11mtom10/|  
|MTOM WS-Policy onaylama|http://www.w3.org/Submission/2006/SUBM-ws-MTOMPolicy-20061101/.|  
  
 Aşağıdaki XML ad alanları ve ilişkili önekleri bu konu boyunca kullanılır.  
  
|önek|Namespace Tekdüzen Kaynak Tanımlayıcısı (URI)|  
|------------|---------------------------------------------------|  
|S11|http://schemas.xmlsoap.org/SOAP/Envelope|  
|s12|http://www.w3.org/2003/05/SOAP-Envelope|  
|wsa|http://www.w3.org/2004/08/Addressing|  
|wsam|http://www.w3.org/2007/05/Addressing/metadata|  
|wsap|http://schemas.xmlsoap.org/ws/2004/09/Policy/Addressing|  
|wsa10|http://www.w3.org/2005/08/Addressing|  
|wsaw10|http://www.w3.org/2006/05/Addressing/WSDL|  
|XOP|http://www.w3.org/2004/08/XOP/include|  
|xmime|http://www.w3.org/2004/06/xmlmime<br /><br /> http://www.w3.org/2005/05/xmlmime|  
dp|http://schemas.microsoft.com/NET/2006/06/Duplex|  
  
## <a name="soap-11-and-soap-12"></a>SOAP 1.1 ve SOAP 1.2  
  
### <a name="envelope-and-processing-model"></a>Zarf ve Model işleme  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Temel Profil 1.1 (BP11) ve temel Profil 1.0 (SSBP10) aşağıdaki SOAP 1.1 Zarf işleme uygular. SOAP 1.2 Zarf SOAP12 bölüm 1 aşağıdaki işlem uygulanır.  
  
 Bu bölümde tarafından gerçekleştirilecek belirli uygulama seçimler açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] BP11 ve SOAP12 bölüm 1 sabittir.  
  
#### <a name="mandatory-header-processing"></a>Zorunlu üstbilgiyi işleme  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]üstbilgiler işleniyor işaretlenmiş için kurallara `mustUnderstand` SOAP 1.1 ve SOAP 1.2 belirtimlere, aşağıdaki farklılıkları açıklanan.  
  
 Girer bir ileti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal yığını ilişkili bağlama öğeleri tarafından örneğin yapılandırılmış tek tek kanalları, ileti metin kodlaması, güvenlik, güvenilir Mesajlaşma ve işlemler tarafından işlenir. Her bir kanala ilişkili ad alanından üstbilgileri tanır ve anladım olarak işaretler. Bir ileti dağıtıcısı girdikten sonra karşılık gelen ileti işlem başına Sözleşme ve bunları anladım işaretleri tarafından beklenen üstbilgileri işlemini biçimlendiricisi okur. Dağıtıcı kalan tüm üstbilgileri değil anladı ancak olarak işaretlenmiş olup olmadığını doğrular sonra `mustUnderstand` ve bir özel durum oluşturur. İçeren iletileri `mustUnderstand` recipient öğesinde hedeflenen üstbilgileri alıcı uygulama kodu tarafından işlenmedi.  
  
 Gibi katmanlı işleme altyapısı katmanları ve SOAP düğümünün uygulama katmanları arasında ayrım sağlar:  
  
-   B1111: değil anlaşılır üstbilgileri tarafından işlenen iletisi sonra algılanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı kanal yığını, ancak uygulama tarafından işlenmeden önce  
  
     `mustUnderstand` Üstbilgi değeri SOAP 1.1 ve SOAP 1.2 arasında farklılık gösterir. Temel Profil 1.1 gerektirir `mustUnderstand` değer 0 veya 1 SOAP 1.1 iletileri için olabilir. SOAP 1.2 sağlar 0, 1, `false`, ve `true` olarak değerleri ancak kurallı gösterimi yayma önerir `xs:boolean` değerleri (`false`, `true`).  
  
-   B1112: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yayar `mustUnderstand` SOAP zarfının değerleri 0 ile 1 SOAP 1.1 ve SOAP 1.2 sürümleri için. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tüm değer alan kabul `xs:boolean` için `mustUnderstand` üstbilgi (0, 1, `false`, `true`)  
  
#### <a name="soap-faults"></a>SOAP hataları  
 Bir listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-belirli bir SOAP hatası uygulamaları.  
  
-   B2121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aşağıdaki SOAP 1.1 hata kodlarını döndürür: `s11:mustUnderstand`, `s11:Client`, ve `s11:Server`.  
  
-   B2122: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aşağıdaki SOAP 1.2 hata kodlarını döndürür: `s12:MustUnderstand`, `s12:Sender`, ve `s12:Receiver`.  
  
### <a name="http-binding"></a>HTTP bağlama  
  
#### <a name="soap-11-http-binding"></a>SOAP 1.1 HTTP bağlama  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Temel Profil 1.1 belirtimini aşağıdaki açıklamalar 3.4 bölümle aşağıdaki SOAP1.1 HTTP bağlaması uygular:  
  
-   B2211: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti, HTTP POST isteklerini yeniden yönlendirilmesini uygulamıyor.  
  
-   B2212: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcileri 3.4.8 uygun olarak HTTP tanımlama bilgilerini destekleyen.  
  
#### <a name="soap-12-http-binding"></a>SOAP 1.2 HTTP bağlama  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]SOAP 1.2 HTTP bağlaması SOAP 1.2 bölümü 2 (SOAP12Part2) belirtimiyle aşağıdaki açıklamalar bölümünde açıklandığı gibi uygular.  
  
 SOAP 1.2 sunulan bir isteğe bağlı eylem parametresi için `application/soap+xml` medya türü. Bu parametre WS adresleme kullanılmadığı SOAP ileti gövdesini ayrıştırılması gerek kalmadan ileti gönderme en iyi duruma getirmek kullanışlıdır.  
  
-   R2221: `application/soap+xml` eylem parametresi SOAP 1.2 istek üzerine varsa eşleşmelidir `soapAction` özniteliği `wsoap12:operation` öğesi içinde karşılık gelen WSDL bağlama.  
  
-   R2222: `application/soap+xml` eylem parametresi, bir SOAP 1.2 iletideki varsa eşleşmelidir `wsa:Action` WS adresleme 2004/08 veya WS adresleme 1.0 ne zaman kullanılır.  
  
 WS-adresleme devre dışıdır ve gelen istek bir eylem parametresinin içermediğinden, ileti `Action` belirtilen olarak sayılmaz.  
  
## <a name="ws-addressing"></a>WS-adresleme  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WS-adresleme 3 sürümlerini uygular:  
  
-   WS-adresleme 2004/08  
  
-   1.0 çekirdek (ADDR10 çekirdekli) ve (SOAP ADDR10) bağlama SOAP adresleme W3C Web Hizmetleri  
  
-   WS-adresleme 1.0 - meta verileri  
  
### <a name="endpoint-references"></a>Uç nokta başvuruları  
 WS-adresleme'nin tüm sürümleri, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulayan uç noktaları tanımlamak için uç nokta başvuruları kullanın.  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a>Uç nokta başvuruları ve WS adresleme sürümleri  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WS-adresleme kullanan altyapı protokolleri ve belirli bir sayı uygulayan `EndpointReference` öğesi ve `W3C.WsAddressing.EndpointReferenceType` sınıfı (örneğin, WS-ReliableMessaging, WS-SecureConversation ve WS-Trust). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Her iki sürümü WS-adresleme diğer altyapı protokollerle kullanımını destekler. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]uç noktaları bir sürümü WS adresleme uç nokta başına destekler.  
  
 R3111, ad alanı için `EndpointReference` öğesi veya türü ile değiştirilen iletilerin kullanılan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç nokta WS adresleme-bu bitiş noktası tarafından uygulanan sürümü aynı olmalıdır.  
  
 Örneğin, varsa bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint uygulayan WS-ReliableMessaging `AcksTo` gibi bir uç nokta içinde tarafından döndürülen üstbilgi `CreateSequenceResponse` WS adresleme sürümünü kullanır, `EncodingBinding` öğesi için bu uç nokta belirtir.  
  
#### <a name="endpoint-references-and-metadata"></a>Uç nokta başvuruları ve meta veriler  
 Çeşitli senaryoları meta veriler veya belirli bir uç nokta için meta veriler için bir başvuru iletişim kurmasını gerektirir.  
  
 B3121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-MetadataExchange (MEX) belirtimi değere veya başvuruya göre meta veri uç noktası başvurular eklemek için Bölüm 6 açıklanan mekanizmaları uygular.  
  
 Bir senaryo düşünün burada bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti Belirteç Verenin http://sts.fabrikam123.com, tarafından verilmiş bir güvenlik onaylar biçimlendirme dili (SAML) belirteci kullanarak kimlik doğrulaması gerektirir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Endpoint kullanarak bu kimlik doğrulama gereksinimini açıklar `sp:IssuedToken` onaylama işlemi bir iç içe `sp:Issuer` Belirteç Verenin işaret eden onaylama. Erişim istemci uygulamaları `sp:Issuer` onaylama Belirteç Verenin bitiş noktası ile iletişim kurma bilmeniz gerekir. İstemcinin meta verileri Belirteç Verenin hakkında bilmek ister. MEX içinde tanımlanmış uç nokta başvuru meta veri uzantılarını kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Belirteç Verenin meta veriler için bir başvuru sağlar.  
  
```xml  
<sp:IssuedToken>  
  <sp:Issuer>  
    <wsa10:Address>  
      http://sts.fabrikam123.com  
    </wsa10:Address>  
    <wsa10:Metadata>  
      <mex:Metadata>  
        <mex:MetadataSection>  
          <mex:MetadataReference>  
            <wsa10:Address>  
              http://sts.fabrikam123.com/mex  
            </wsa10:Address>  
          </mex:MetadataReference>  
        </mex:MetadataSection>  
      </mex:Metadata>  
    </wsa10:Metadata>  
  </sp:Issuer>  
</sp:IssuedToken>  
```  
  
### <a name="message-addressing-headers"></a>İleti adresleme üstbilgileri  
  
#### <a name="message-headers"></a>İleti üstbilgileri  
 Her iki WS adresleme sürümleri için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aşağıdaki ileti üstbilgilerini belirtimleri tarafından belirlenen şekilde kullanır `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, ve `wsa:RelatesTo`.  
  
 B3211: WS adresleme tüm sürümleri için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] korur, ancak ileti üstbilgilerini WS adresleme kutudan çıktığı oluşturmadığı `wsa:FaultTo` ve `wsa:From`.  
  
 Etkileşim uygulamaları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar, bu ileti üstbilgilerini ekleyebilir ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] buna uygun olarak işleyecek.  
  
#### <a name="reference-parameters-and-properties"></a>Başvuru parametreleri ve özellikleri  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]uç nokta başvuru parametreleri ve başvuru p Implements işlenmesini  
  
 ilgili belirtimlerine uygun olarak özellikleri.  
  
 B3221: WS adresleme 2004/08 kullanmak üzere yapılandırıldığında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktalar değil ayırt başvuru özellikleri ve başvuru parametreleri işleme arasında.  
  
### <a name="message-exchange-patterns"></a>İleti Exchange desenleri  
 Web hizmeti işlemi çağırma yer alan iletileri dizisi olarak adlandırılır *ileti değişim deseni*. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tek yönlü destekler, istek-yanıt ve çift yönlü iletisi desenleri exchange. Bu bölümde kullanılan ileti değişim deseni bağlı olarak işleme iletideki WS adreslendirme gereksinimleri açıklar.  
  
 Bu bölümde genelinde istek sahibinin ilk ileti gönderir ve Yanıtlayıcı ilk iletiyi alır.  
  
#### <a name="one-way-message"></a>Tek yönlü iletisi  
 Zaman bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint iletilerle desteklemek üzere yapılandırılmış bir belirli `Action` tek yönlü bir deseni izlemesini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktası aşağıdaki aşağıdaki davranışları ve gereksinimleri. WS-adresleme her iki sürümü de desteklenen aksi belirtilmediği sürece, davranışları ve kuralları uygula [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R3311: İstek sahibinin içermelidir `wsa:To`, `wsa:Action`ve uç nokta başvuru tarafından belirtilen tüm başvuru parametreleri için üstbilgiler. Ne zaman WS adresleme 2004/08 kullanılır ve karşılık gelen üstbilgileri iletiye çok eklenmelidir [başvuru Özellikleri] uç nokta başvuruya göre belirtilir.  
  
-   B3312: İstek sahibinin içerebilir `MessageID`, `ReplyTo`, ve `FaultTo` üstbilgileri. Alıcı altyapı bunları göz ardı eder ve uygulamaya geçirilir.  
  
-   R3313: HTTP kullanılır ve hiçbir ileti üzerinde HTTP yanıt leg gönderilen Yanıtlayıcı boş bir gövde ve bir HTTP 202 durum kodu ile bir HTTP yanıtının göndermeniz gerekir.  
  
     HTTP taşıma kullanımda ve işlem sözleşmesi bir ileti tek yönlü bildirir, HTTP yanıtı hala altyapı ileti göndermek için kullanılabilir — örneğin, güvenilir Mesajlaşma gönderebilirsiniz bir `SequenceAcknowledgement` bir HTTP yanıt iletisi.  
  
-   B3314: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı göndermez bir hata iletisi tek yönlü iletisine yanıt olarak.  
  
#### <a name="request-reply"></a>İstek-Yanıt  
 Zaman bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bitiş noktası içeren bir ileti için yapılandırılmış bir belirli `Action` istek-yanıt deseni izlemesini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktası aşağıdaki davranışları ve aşağıdaki gereksinimleri. WS-adresleme her iki sürümü de desteklenen aksi belirtilmediği sürece, davranışları ve kuralları uygula [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R3321: İstek sahibinin istekte içermelidir `wsa:To`, `wsa:Action`, `wsa:MessageID`ve tüm başvuru parametreleri başvuru özellikler (veya her ikisi) uç noktası başvuru tarafından belirtilen için üstbilgiler.  
  
-   R3322: WS adresleme 2004/08 kullanıldığında `ReplyTo` istekte de eklenmelidir.  
  
-   R3323: WS adresleme 1.0 kullanıldığında ve `ReplyTo` olduğu istekte mevcut değil, varsayılan uç nokta başvuru "http://www.w3.org/2005/08/addressing/anonymous" eşit [address] özelliği ile kullanılır.  
  
-   R3324: İstek sahibinin içermelidir `wsa:To`, `wsa:Action`, ve `wsa:RelatesTo` yanıt iletisi üstbilgilerinde yanı sıra tüm başvuru parametreleri başvuru özellikler (veya her ikisi) tarafından belirtilen üstbilgilerini `ReplyTo` bitiş noktası başvurusu İstek.  
  
### <a name="web-services-addressing-faults"></a>Adresleme hataları Web Hizmetleri  
 R3411: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS adresleme 2004/08 tarafından tanımlanan aşağıdaki hataları üretir.  
  
|Kod|Sebep|  
|----------|-----------|  
|wsa:DestinationUnreachable|İleti ile ulaştığında bir `ReplyTo` bu kanal için kurulmuş yanıt adresinden farklı; Kime üstbilgisinde belirtilen adresten dinleme bitiş noktası yoktur.|  
|wsa:ActionNotSupported|Altyapı kanalları ya da uç noktasıyla ilişkili dağıtıcısı belirtilen eylem algılamaz `Action` üstbilgi.|  
  
 R3412: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS adresleme 1.0 tarafından tanımlanan aşağıdaki hataları üretir.  
  
|Kod|Sebep|  
|----------|-----------|  
|wsa10:InvalidAddressingHeader|Yinelenen `wsa:To`, `wsa:ReplyTo`, `wsa:From` veya `wsa:MessageID`. Yinelenen `wsa:RelatesTo` aynı `RelationshipType`.|  
|wsa10:MessageAddressingHeaderRequired|Gerekli adresleme üstbilgisi eksik.|  
|wsa10:DestinationUnreachable|İleti ile ulaştığında bir `ReplyTo` bu kanal için kurulmuş yanıt adresinden farklı. Kime üstbilgisinde belirtilen adresten dinleme bitiş noktası yoktur.|  
|wsa10:ActionNotSupported|Belirtilen eylem `Action` üstbilgi altyapı kanalları ya da uç noktasıyla ilişkili dağıtıcı tarafından tanınmıyor.|  
|wsa10:EndpointUnavailable|Uç nokta incelenmesi temel sıralı işlemez belirten bu hataya geri RM kanalı gönderir `CreateSequence` ileti üstbilgilerini adresleme.|  
  
 Yukarıdaki tablolarda kod eşlemeleri için `FaultCode` içinde SOAP 1.1 ve `SubCode` (koduyla gönderen =) SOAP 1.2 içindeki.  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 bağlama ve WS-ilke onaylamalarını  
  
#### <a name="indicating-use-of-ws-addressing"></a>WS-adresleme kullanımını gösteren  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]özel bir WS adresleme sürüm için uç nokta destek belirtmek için ilke onaylamalarını kullanır.  
  
 Aşağıdaki ilke onaylama uç nokta İlkesi konu [WS-PA] ve gönderilen ve uç noktasından alınan iletileri WS adresleme 2004/08 kullanmalısınız gösterir.  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 Bu ilke onaylama WS adresleme 2004/08 belirtimi artırmaktadır.  
  
 Bu, gönderilen ve alınan iletileri gösterir aşağıdaki ilke onaylama WS adresleme 1.0 kullanmanız gerekir.  
  
```xml
<wsam:Addressing/>   
```  
  
 Aşağıdaki ilke onaylama bir uç nokta İlkesi konu [WS-PA] ve gönderilen ve uç noktasından alınan iletileri WS adresleme 2004/08 kullanması gerektiğini belirtir.  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 `wsaw10:UsingAddressing` Öğesi [WS-adresleme-WSDL] ödünç ve WS-Policy bağlamında bu belirtimi uyumlu kullanılır, Bölüm 3.1.2.  
  
 Adresleme kullanımını WSDL 1.1, SOAP 1.1 ve SOAP 1.2 HTTP bağlamaları semantiği değiştirmez. Bir yanıt adresleme ve WSDL SOAP 1.x HTTP bağlama kullanan bir uç nokta için gönderilen bir istek bekleniyorsa, örneğin, yanıt HTTP yanıtı kullanarak gönderilmelidir.  
  
 Http yanıtı gönderilen yanıtlar için WS-AM onayı ifade eder:  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 Tam İlkesi onaylama şuna benzeyebilir:  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 Ancak, istek sahibinin ve Yanıtlayıcı Yanıtlayıcı tarafından gönderilen Örneğin, istenmeyen tek yönlü iletileri arasında kurulan iki bağımsız ters HTTP bağlantılarını kalmaktan fayda ileti exchange desenleri vardır.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]iki temel taşıma kanalları burada bir kanal giriş iletileri için kullanılır ve çıktı iletiler için kullanılan başka bir bileşik çift yönlü kanal kurabilir bir özellik sunar. HTTP taşıma söz konusu olduğunda, bileşik çift yönlü iki ters HTTP bağlantılarını sağlar. Yanıtlayıcı iletileri göndermek için bir bağlantı istek sahibinin kullanır ve Yanıtlayıcı diğer iletiler istemciye geri gönderilecek kullanır.  
  
 Ayrı http istekleri üzerinden gönderilen yanıtlar için ws-am onayı ifade eder  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 Tam İlkesi onaylama şuna benzeyebilir:  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 Talep sahibinin Yanıtlayıcı ve istekte bulunan kişinin Yanıtlayıcı akan iletileri için kullanılacak iki ayrı ters HTTP bağlantılarını WSDL 1.1 SOAP 1.x HTTP bağlamaları kullanan uç noktalarda uç nokta İlkesi konu [WS-PA] olan aşağıdaki onay kullanımını, sırasıyla.  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 Önceki deyimi aşağıdaki gereksinimleri müşteri adayları `wsa:ReplyTo` başlığı istek iletileri için:  
  
-   R3514: bir bitiş noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle `[address]` özelliği eşit değil "http://www.w3.org/2005/08/addressing/anonymous" uç nokta WSDL 1.1 SOAP 1.x HTTP bağlama kullanır ve bir ilke alternatif ile varsa bir `wsap10:UsingAddressing` veya `wsap:UsingAddressing` onaylama eşleşmiş ile `cdp:CompositeDuplex` bağlı.  
  
-   R3515: bir bitiş noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle `[address]` özelliği eşit "http://www.w3.org/2005/08/addressing/anonymous" ya da yok bir `ReplyTo` tümü, uç nokta WSDL 1.1 kullanıyorsa, üst bilgisi SOAP 1.x HTTP bağlama ve bir ilke alternatif ile sahip `wsap10:UsingAddressing` onaylama ve Hayır `cdp:CompositeDuplex` bağlı onaylama.  
  
-   R3516: bir bitiş noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle bir `[address]` özelliği "uç nokta WSDL 1.1 SOAP 1.x HTTP bağlama kullanır ve bir ilke alternatif ilevarsahttp://www.w3.org/2005/08/addressing/anonymous"eşit`wsap:UsingAddressing` onaylama ve Hayır `cdp:CompositeDuplex` bağlı onaylama.  
  
 Bir öğenin sunarak benzer protokolü bağlamaları tanımlamak WS adresleme WSDL belirtimi çalışır `<wsaw:Anonymous/>` değerlerle üzerinde gereksinimleri göstermek için üç metinsel (gerekli, isteğe bağlı ve yasaklanmış) `wsa:ReplyTo` üstbilgi (Bölüm 3.2). Ne yazık ki, bu tür bir öğe onayı ifade kullanarak alternatifleri kesişimi desteklemek için etki alanına özgü uzantılar gerektirdiğinden böyle öğesi tanımı bir onaylama WS-İlkesi ' nin bağlamında özellikle kullanılabilir değil. Bu tür öğesi tanımı değerini de gösterir `ReplyTo` HTTP aktarımı için belirli kolaylaştırır Tel üzerinde uç noktası davranışı aksine üstbilgi.  
  
#### <a name="action-definition"></a>Eylem tanımı  
 WS-adresleme 2004/08 tanımlayan bir `wsa:Action` için öznitelik `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` öğeleri. WS-adresleme 1.0 WSDL bağlama (WS-ADDR10-WSDL) benzer bir öznitelik tanımlar `wsaw10:Action`.  
  
 İkisi arasındaki tek fark sırasıyla Bölüm WS-ADDR 3.3.2 ve WS-ADDR10-WSDL 4.4.4 bölümünde açıklanan varsayılan eylem düzeni semantiği ' dir.  
  
 Aynı paylaşan iki uç nokta uygun olan `portType` (veya sözleşme, içinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terminolojisi) ancak WS adresleme farklı sürümlerini kullanan. Ancak eylem tarafından tanımlanan o `portType` ve uygulayan uç noktalar arasında değiştirmemelisiniz `portType`, her iki varsayılan eylem desenleri desteklemesini mümkün olur.  
  
 Bu controversy gidermek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tek bir sürümünü destekleyen `Action` özniteliği.  
  
 B3521: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanan `wsaw10:Action` özniteliği `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` WS-ADDR10-belirlemek için WSDL içinde tanımlanan öğeleri `Action` bitiş noktası tarafından kullanılan WS adresleme sürümü yedeklemiş karşılık gelen iletiler için URI.  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a>Kullanım uç noktası başvuru iç WSDL bağlantı noktası  
 WS ADDR10 WSDL bölüm 4.1 genişletir `wsdl:port` eklenecek öğe `<wsa10:EndpointReference…/>` uç nokta WS adresleme koşullarını tanımlamak için alt öğesi. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Bu yardımcı program WS adresleme 2004/08 üzerinde genişletir izin vererek `<wsa:EndpointReference…/>` bir alt öğesi görüntülenmesini `wsdl:port`.  
  
-   R3531: iliştirilmiş ilke alternatif bir uç nokta varsa, bir `<wsaw10:UsingAddressing/>` ilgili ilke onaylama `wsdl:port` öğesi bir alt öğesi içerebilir `<wsa10:EndpointReference …/>`.  
  
-   R3532: Varsa bir `wsdl:port` bir alt öğe içeriyor `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` alt öğe değeri değerini eşleşmelidir `@address` eşdüzey özniteliği `wsdl:port` / `wsdl:location` öğesi.  
  
-   R3533: bir uç nokta iliştirilmiş ilke alternatif varsa `<wsap:UsingAddressing/>` ilgili ilke onaylama `wsdl:port` öğesi bir alt öğesi içerebilir `<wsa:EndpointReference …/>`.  
  
-   R3534: Varsa bir `wsdl:port` bir alt öğe içeriyor `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` alt öğe değeri değerini eşleşmelidir `@address` eşdüzey özniteliği `wsdl:port` / `wsdl:location` öğesi.  
  
### <a name="composition-with-ws-security"></a>WS güvenliği ile oluşturma  
 WS-ADDR ve WS-ADDR10 güvenlik göz önünde bulundurarak bölümlere göre tüm adresleme ileti üstbilgilerini birlikte ileti gövdesi birbirine bağlamak için imzalanması için önerilir.  
  
 WS güvenliği ileti bütünlüğü koruma için kullanıldığında, ileti gövdesi birlikte WS adresleme ileti üstbilgilerini yanı sıra üstbilgileri başvuru parametreleri veya özellikler (veya her ikisi de) sonuçlandı imzalanması gerekir.  
  
### <a name="examples"></a>Örnekler  
  
#### <a name="one-way-message"></a>Tek yönlü iletisi  
 Bu senaryoda, gönderenin alıcı için tek yönlü bir ileti gönderir. SOAP 1.2, HTTP 1.1 ve 1.0 W3C WS adresleme kullanılır.  
  
 İstek iletisi yapısı: İleti üstbilgilerini dahil `wsa10:To` ve `wsa10:Action` öğeleri. Belirli bir ileti gövdesini içeren `<app:Ping>` uygulama ad alanından öğesi.  
  
 HTTP üstbilgileri: POST hedef URI eşleşen `wsa10:To` öğesi.  
  
 Content-Type üstbilgisi değeri olan `application/soap+xml` SOAP 1.2 gerektirdiği. Parametreleri `charset` ve `action` dahil edilir. `action` Content-Type üstbilgisi parametresinin değeri ile eşleşen `wsa10:Action` ileti üstbilgisi.  
  
```  
POST http://fabrikam123.com/Service HTTP/1.1  
Content-Type: application/soap+xml; charset=utf-8;    
              action="http://fabrikam123.com/Service/OneWay"  
Host: 131.107.72.15  
Content-Length: 1501  
Expect: 100-continue  
Proxy-Connection: Keep-Alive  
<s12:Envelope>  
  <s12:Header>  
    <wsa10:To s12:mustUnderstand="1">  
        http://fabrikam123.com/Service  
    </wsa10:To>  
    <wsa10:Action s12:mustUnderstand="1">  
        http://fabrikam123.com/Service/OneWay   
    </wsa10:Action>  
  </s12:Header>  
  <s12:Body>  
    <Ping xmlns="http://fabrikam123.com/Service/">  
      <Text>Hello World</Text>  
    </Ping>  
  </s12:Body>  
</s12:Envelope>  
```  
  
 Alıcı boş HTTP yanıt ve durum 202 ile yanıt verir. HTTP yanıt örneği:  
  
```  
HTTP/1.1 202 Accepted  
Date: Fri, 15 Jul 2005 08:56:07 GMT  
Server: Microsoft-IIS/6.0  
MicrosoftOfficeWebServer: 5.0_Pub  
X-Powered-By: ASP.NET  
X-AspNet-Version: 2.0.50215  
Cache-Control: private  
Content-Length: 0  
```  
  
## <a name="soap-message-transmission-optimization-mechanism"></a>SOAP iletisi iletim iyileştirme mekanizması  
 Bu bölümde açıklanmıştır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP SOAP MTOM uygulama ayrıntıları. MTOM teknolojidir SOAP iletisi kodlama mekanizması geleneksel text/XML kodlama olarak aynı sınıfın veya [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ikili kodlama. MTOM aşağıdakileri içerir:  
  
-   Bir XML kodlama ve [XOP] tarafından açıklanan paketleme mekanizması ayrı ikili parçalara base64 ile kodlanmış ikili veri içeren XML bilgi öğeleri iyileştirir.  
  
-   MIME kapsülleme XML bilgi ve her ikili XOP paketinin parçası ayrı bir MIME bölüm içinde serileştiren XOP paketi.  
  
-   SOAP için uygulanan bir MIME XOP kodlama 1.x Zarf.  
  
-   Bir HTTP aktarım bağlama.  
  
 MTOM olmayan HTTP taşımaları ile birlikte kullanmak da mümkündür [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Ancak, bu konudaki şu HTTP odaklanır.  
  
 MTOM biçim belirtim MTOM kendisi, XOP ve MIME kapsayan büyük kümesi yararlanır. Bu belirtimi kümesinin modülerlik biçimi ve işleme semantiğini tam gereksinimlerine yeniden oluşturmak biraz zor hale getirir. Bu bölümde MTOM HTTP bağlaması için biçimi ve işleme gereksinimleri açıklanmaktadır.  
  
### <a name="mtom-message-encoding"></a>İleti MTOM kodlama  
  
#### <a name="generating-mtom-messages"></a>MTOM iletileri oluşturma  
 [XOP] bölümü 3.1 bağlamalarında tanımlanmış bir XOP pakete base64 değerler içeren öğesi bilgi öğelerle XML kodlama işlemi açıklanır.  
  
 Aşağıdaki adımlar dizisini özel MTOM kodlama işlemi açıklanmaktadır:  
  
1.  Kodlanacak SOAP Zarfı hiçbir öğe bilgi öğe ile içerdiğinden emin olun bir `[namespace name]` "http://www.w3.org/2004/08/xop/include" olarak ve bir `[local name]` , `Include`.  
  
2.  Boş bir MIME paketi oluşturun.  
  
3.  Özgün XML bilgi içinde en iyi duruma getirilmesi öğesi bilgi öğeleri tanımlayın. Öğeleri en iyi duruma getirilmesi karakterleri oluşturan `[children]` öğesi bilgilerinin öğesi kurallı biçiminde olmalı `xs:base64Binary` (XSD-2, 3.2.16 bkz base64Binary) ve, satır içi, önceki herhangi bir boşluk karakteri içermemelidir veya boşluk olmayan içerik aşağıdaki.  
  
4.  Özgün SOAP Zarfı kopyası olan bir XOP SOAP Zarfı oluşturun, ancak her öğe bilgileri alt öğeleri önceki adımda belirlediğiniz öğesi olarak değiştirilir. bir `xop:Include` olarak öğe bilgi öğe:  
  
    1.  Değiştirilen karakterleri base64 kodlu veriler olarak işleyerek ikili verisine dönüştürür.  
  
    2.  R3133 ve R3134 gereksinimleri karşılayan benzersiz bir Content-ID üstbilgi değeri oluşturur.  
  
    3.  İkili değeri olan bir Content-Transfer-Encoding MIME üstbilgisi oluşturur.  
  
    4.  Öğe bilgileri öğe iyileştirilen varsa ([üst] yeni eklenen `xop:Include` öğe bilgi öğe) sahip bir `xmime:contentType` özniteliği bilgi öğesi, bir Content-Type MIME üstbilgisi değeri ile oluşturun `xmime:contentType` özniteliği.  
  
    5.  İşlenen base64, 4b Content-ID başlığından, 4 c, adım 4 d oluşturursa Content-Type üstbilgisi Content-Transfer-Encoding başlığından değiştirilen karakter gelen kodunu çözdü ikili verileri tarafından oluşturulmuş içeriğe sahip yeni bir ikili MIME bölümü oluşturur.  
  
    6.  Ekleme bir `href` özniteliğini `xop:Include` değeri CID bir öğesiyle: 4b adımında oluşturulan Content-ID üstbilgi değeri türetilen URI. Kapsayan Kaldır "\<" ve ">" URL-kalan dize ve önekini ekleyin kaçış karakterleri `cid:`. Aşağıdaki minimum karakter kümesi RFC1738 ve RFC2396 tarafından Atlanan için gereklidir. Diğer karakterler kaçışlı.  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  Adım 4 XOP SOAP Zarfı içeren bir kök MIME bölümü oluşturun.  
  
6.  HTTP Content-Type üstbilgisi de dahil olmak üzere HTTP üst bilgilerini yazın.  
  
7.  MIME paket yazma.  
  
#### <a name="processing-mtom-messages"></a>MTOM iletileri işleme  
 Bir MTOM işleme ileti tam önceki açıklanan sürecin tersidir "üretme MTOM iletileri" bölümü:  
  
1.  Kök MIME bölümü Content-Type olduğundan `application/xop+xml`.  
  
2.  SOAP zarfını paketi bir XML belgesi olarak MIME parçası kök ayrıştırarak oluşturun. Karakter kodlamasını tarafından belirlenir `charset` Kök MIME bölümü Content-Type parametresi.  
  
3.  Oluşturulan SAOP zarfına her öğe bilgi öğe için olan, kendi [alt] özelliğini tek üyesi olarak bir `xop:Include` öğe bilgi öğe:  
  
    1.  Kaldırma `cid:` öneki ve tüm URI kaçış sıraları (RFC 2396) değerinde unescape `@href` özniteliği `xop:Include` öğesi. Sonuç dizesinde alın "\<", ">".  
  
    2.  Adım 3a türetilmiş dizesiyle eşleşen Content-ID üstbilgi değeri olan MIME bölümü bulun.  
  
    3.  Değiştir `xop:Include` görünür öğe bilgi öğe `children` kurallı base64 kodlaması temsil karakter bilgi öğelerinin bulunduğu her öğesinin özelliği (XSD-2, 3.2.16 bkz base64Binary) MIME bölümü varlık gövdesinin Adım 3b'de tanımlanan (etkili bir şekilde yerine `xop:Include` öğe bilgi öğe paket bölümünden yeniden verilerle).  
  
#### <a name="http-content-type-header"></a>HTTP Content-Type üstbilgisi  
 Bir listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] SOAP 1.x MTOM olarak kodlanmış bir ileti HTTP Content-Type üstbilgisinin biçimi için açıklamalar MTOM belirtimi kendisini belirtilen gereksinimleri türetilmiş ve MTOM ve RFC 2387 türetilir.  
  
-   R4131: Bir HTTP Content-Type üstbilgisi değeri multipart/related (büyük küçük harf duyarsız) ve parametrelerini olmalıdır. Parametre adları büyük/küçük harfe duyarsızdır. Parametre sırası önemli değildir.  
  
-   Content-Type üstbilgisi MIME iletileri için tam Backus-Naur formu'nı (BNF) bölümü 5.1, RFC 2045 listelenir.  
  
-   R4132: Bir HTTP Content-Type üstbilgisi değeri olan bir tür parametresi olmalıdır `application/xop+xml` çift tırnak işaretleri içine alınmalıdır.  
  
 Çift tırnak işaretleri kullanma zorunluluğu RFC 2387 açık olmamasına karşın, tüm parametreleri büyük olasılıkla içeren multipart/related medya türü gibi karakterler ayrılmış metin gözlemleyen "@" or "/" ve bu nedenle çift tırnak işareti gerekiyor.  
  
-   R4133: Başlangıç parametresi SOAP içeren MIME bölümü Content-ID üstbilgisi değeri ile bir HTTP Content-Type üstbilgisi olmalıdır 1.x Zarf, çift tırnak işaretleri içine alınmalıdır. Başlangıç parametresi atlanırsa, ilk MIME bölümü SOAP içermelidir 1.x Zarf.  
  
-   R4134: Text/xml, çift tırnak işaretleri içine değeriyle başlangıç bilgileri parametresi SOAP 1.1 kodlanmış MTOM iletisi için bir HTTP Content-Type üstbilgisi eklemeniz gerekir.  
  
-   R4135: SOAP 1.2 MTOM olarak kodlanmış bir ileti için bir HTTP Content-Type üstbilgisi değeri başlatma bilgisi parametresiyle içermelidir `application/soap+xml`, çift tırnak işaretleri içine alarak.  
  
-   R4136: HTTP Content-Type üstbilgisi SOAP 1.x MTOM olarak kodlanmış bir ileti için sınır parametresi BNF bölüm 5.1.1, RFC 2046 tanımlanmış MIME sınır eşleşen (çift tırnak işaretleri içine) değerine sahip olması gerekir  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     Örnekler:  
  
     DÜZELTİN  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     DÜZELTİN  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     YANLIŞ  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a>Bilgi MIME bölümü  
 SOAP zarfını XOP MIME paketinin kök bir parçası kapsüllenmiş ve genellikle adlı 1.x `infoset` bölümü.  
  
-   R4141: SOAP adlı XOP MIME paketi kök bir parçası olarak Zarf kapsüllenmiş 1.x `infoset` bölümü ve gelen HTTP Content-Type başvurulan.  
  
-   R4142: SOAP `Infoset` bölümü aşağıdaki MIME Üstbilgileri içermelidir: `Content-ID`, `Content-Transfer-Encoding`, ve `Content-Type`.  
  
 Content-ID üstbilgi biçimi RFC 2045 tanımlanır  
  
```  
"Content-ID" ":" msg-id  
```  
  
 Burada `msg-id` (yani RFC 822, RFC 2045 başvurulan yerini) RFC 2822 olarak tanımlanır:  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 ve etkili bir şekilde bir e-posta adresi içine alınmış "\<" ve ">". `[CFWS]` Önek ve sonek 2822 açıklamaları taşımak için RFC eklendi ve birlikte çalışabilirlik korumak için kullanılmamalıdır.  
  
 R4143: Bilgi MIME bölümü Content-ID üstbilgisinin değerini izlemelisiniz `msg-id` ile RFC 2822 üretimden `[CFWS]` atlanmış önek ve sonek bölümleri.  
  
 MIME uygulamaları sayısı rahat gereksinimleri içine alınmış bir değer için "\<" ve ">" bir e-posta adresi ve kullanılan `absoluteURI` içine "\<", ">" e-posta adresi yanı sıra. Bu sürümü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] formun Content-ID MIME üstbilgi değerleri kullanır:  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 R4144: Content-ID üstbilgi değerleri aşağıdaki rahat eşleşen MTOM işlemciler kabul etmelidir `msg-id`.  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 MIME (RFC 2045) MIME bölümü içeriğini kodlama iletişim kurmak için Content-Transfer-Encoding üstbilgisi sağlar. Content-Transfer-Encoding için tanımlanan varsayılan içerik Transfer-Encoding üstbilgisi büyük birlikte çalışabilirlik için gerektiği şekilde SOAP iletilerin çoğu için uygun olmayan 7 bit:  
  
-   R4145: İçeriği Transfer-Encoding üstbilgisi SOAP bilgi bölümü içermelidir.  
  
-   R4146: SOAP Zarfı karakter kodlamasını UTF-8 ise Content-Transfer-Encoding üstbilgisinin değerini 8 bit olmalıdır.  
  
-   R4147: UTF-16 karakter kodlamasını SOAP Zarfı varsa, içeriği Transfer-Encoding üstbilgisinin değerini ikili olmalıdır.  
  
-   [XOP göre] bölüm 5,  
  
-   Tür parametreleri ve R4148: Content-Type üstbilgisi medya türü uygulama/xop + xml ile SOAP1.1 bilgi bölümü içermelidir = "text/xml" ve charset  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   R4149: Medya türüyle Content-Type üstbilgisi SOAP 1.2 bilgi bölümü içermelidir `application/xop+xml` ve tür parametreleri = "`application/soap+xml`" ve `charset`.  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     XOP açıklarken `charset` parametresi için `application/xop+xml` isteğe bağlı olacak şekilde birlikte çalışabilirliğini BP 1.1 gereksinimini benzer gerektiğinde `charset` parametresi için `text/xml` medya türü.  
  
-   R41410: `type` ve `charset` parametreleri SOAP 1.x bilgi bölümü Content-Type üstbilgisi mevcut olmalıdır.  
  
#### <a name="wcf-endpoint-support-for-mtom"></a>WCF Bitiş noktası MTOM desteği  
 Base64 ile kodlanmış verileri en iyi duruma getirmek için bir SOAP iletisi kodlanacak MTOM amacı budur. Kısıtlamaları listesi aşağıdadır:  
  
-   R4151: base64 ile kodlanmış verileri içeren herhangi bir öğe bilgi öğesini en iyi duruma.  
  
-   B4152: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] base64 ile kodlanmış verileri içeren ve uzunluğu 1024 bayt aşan öğesi bilgi öğeleri en iyi duruma getirir.  
  
 A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MTOM kullanmak üzere yapılandırılmış uç nokta her zaman MTOM olarak kodlanmış iletileri gönder. Hiçbir bölümleri gereken ölçütleri karşılayan olsa bile, ileti (SOAP Zarfı içeren tek bir MIME bölümü ile bir MIME paketi olarak serileştirilmiş) hala MTOM kodlanır.  
  
### <a name="ws-policy-assertion-for-mtom"></a>MTOM WS-Policy onaylama  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]MTOM kullanım bitiş noktası tarafından belirtmek için aşağıdaki ilke onaylama kullanır:  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   R4211: Önceki ilke onaylama bir uç nokta İlkesi konu ve gönderilen ve uç noktasından alınan tüm iletileri MTOM kullanılarak iyileştirilmiş gerekir belirtir.  
  
-   B4212: MTOM iyileştirme'yi kullanmak üzere yapılandırıldığında bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint karşılık gelen iliştirilmiş ilke MTOM İlkesi onaylama ekler `wsdl:binding`.  
  
### <a name="composition-with-ws-security"></a>WS güvenliği ile oluşturma  
 MTOM mekanizmasıdır benzer bir kodlama `text/xml` ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ikili XML. MTOM sunar doğal birleşim WS güvenliği ve diğer WS-* protokolleri: WS güvenliği kullanarak güvenli bir ileti MTOM kullanılarak iyileştirilebilir.  
  
### <a name="examples"></a>Örnekler  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>WCF SOAP 1.1 ileti MTOM kullanılarak kodlanmış  
  
```  
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1  
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"  
Content-Type: multipart/related;type="application/xop+xml";  
              start="<http://tempuri.org/0>";start-info="text/xml";  
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
Host: 131.107.72.15  
Content-Length: 1501  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
Content-ID: <http://tempuri.org/0>  
Content-Transfer-Encoding: 8bit  
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Body>  
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">  
      <array>  
        <xop:Include   
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"   
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
      </array>  
    </EchoBinaryAsString>  
  </s:Body>  
</s:Envelope>  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
Content-ID: <http://tempuri.org/1/632618206521093670>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
…Binary Content..  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
```  
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>MTOM kullanılarak ileti WCF güvenli SOAP 1.2 kodlanmış  
 Bu örnekte, bir ileti MTOM ve WS-Security tarafından korunan SOAP 1.2 kullanılarak kodlanır. Kodlama içeriğini için tanımlanan ikili parçaları `BinarySecurityToken`, `CipherValue` , `EncryptedData` karşılık gelen şifrelenmiş imza ve şifrelenmiş gövde. Unutmayın `CipherValue` , `EncryptedKey` en iyi duruma getirme tarafından tanımlanmadı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], uzunluğu sonra daha az 1024 bayt olduğundan.  
  
```  
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1  
Content-Type: multipart/related; type="application/xop+xml";  
              start="<http://tempuri.org/0>";  
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";  
              start-info="application/soap+xml";   
              action="http://xmlsoap.org/echoBinaryAsString"  
Host: 131.107.72.15  
Content-Length: 1941  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/0>  
Content-Transfer-Encoding: 8bit  
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
  <s:Header>  
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">  
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>  
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>  
      </u:Timestamp>  
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">  
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
      </o:BinarySecurityToken>  
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>  
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
          <o:SecurityTokenReference>  
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>  
          </o:SecurityTokenReference>  
        </KeyInfo>  
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>  
        </e:CipherData>  
      </e:EncryptedKey>  
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">  
        <o:SecurityTokenReference>  
          <o:Reference URI="#_1"/>  
        </o:SecurityTokenReference>  
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>  
      </c:DerivedKeyToken>  
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:DataReference URI="#_3"/>  
        <e:DataReference URI="#_4"/>  
      </e:ReferenceList>  
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>  
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
          <o:SecurityTokenReference>  
            <o:Reference URI="#_2"/>  
          </o:SecurityTokenReference>  
        </KeyInfo>  
        <e:CipherData>  
          <e:CipherValue>  
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
          </e:CipherValue>  
        </e:CipherData>  
      </e:EncryptedData>  
    </o:Security>  
  </s:Header>  
  <s:Body u:Id="_0">  
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>  
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
          <o:Reference URI="#_2"/>  
        </o:SecurityTokenReference>  
      </KeyInfo>  
      <e:CipherData>  
        <e:CipherValue>  
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
        </e:CipherValue>  
      </e:CipherData>  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/1/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary content of BinarySecurityToken - X509 Certificate...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/2/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary serialization of the encrypted primary signature...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/3/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary serialization of the encrypted Body...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--  
```
