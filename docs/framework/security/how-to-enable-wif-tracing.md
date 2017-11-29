---
title: "Nasıl yapılır: WIF izlemeyi etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 516e065bc360538e7b62807a5492c0c6c9d16e69
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-wif-tracing"></a>Nasıl yapılır: WIF izlemeyi etkinleştirme
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu yöntem, bir ASP.NET uygulamasında WIF izlemeyi etkinleştirmek için ayrıntılı adım adım yordamlar sağlar. Günlük doğru şekilde çalıştığını ve ayrıca İzleme dinleyicisi doğrulamak için uygulamayı test etme yönergeleri sağlar. Bu 'Nasıl Yapılır' konusunda bir Güvenlik Belirteci Hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bunun yerine Kimlik ve Erişim aracı ile birlikte gelen Geliştirme STS'si kullanılır. Geliştirme STS'si gerçek kimlik doğrulaması yapmaz ve yalnızca test amaçlarına yöneliktir. Bu 'Nasıl Yapılır' konusunu tamamlamak için Kimlik ve Erişim aracını yüklemeniz gerekir. Şu konumdan indirilebilir: [kimlik ve erişim aracı](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
> [!IMPORTANT]
>  Pasif uygulamalar için WIF izlemeyi etkinleştirme, diğer bir deyişle, WS-Federasyon protokolünü kullanan uygulamalar olası sunabilir kötü amaçlı bir tarafa (DoS) hizmet reddi saldırılarını veya bilgilerin açığa çıkmasına uygulama. Bu, pasif RPs ve Pasif STSes içerir. Bu nedenle, WIF izleme edilgen RPs veya STSes için bir üretim ortamında etkinleştirmenizi değil öneririz.  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Genel Bakış  
  
-   Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve izlemeyi etkinleştirme  
  
-   2. adım – çözümünüzü  
  
## <a name="objectives"></a>Amaçlar  
  
-   WIF ve geliştirme STS kimlik ve erişim aracı kullanan basit bir ASP.NET uygulaması oluşturma  
  
-   İzlemeyi etkinleştirmek ve çalışır durumda olduğunu doğrulayın  
  
## <a name="overview"></a>Genel Bakış  
 İzleme, hata ayıklama ve türlerde WIF belirteçleri, tanımlama bilgileri, talepler, protokol iletilerini ve daha da dahil olmak üzere, sorunları gidermenize olanak sağlar. WIF izleme WCF izlemeyi benzer; Örneğin, her şeyi kritik iletileri için tüm iletileri görüntülemek için izlemeleri ayrıntı seçebilirsiniz. WIF izlemeleri oluşturulabilir **.xml** dosyaları veya **.svclog** hizmet izleme Görüntüleyicisi aracı kullanarak görüntülenebilir dosyaları. Bu araç bulunan **bin** Windows SDK yükleme dizini yolu bilgisayarınızda, örneğin: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve izlemeyi etkinleştirme  
  
-   2. adım – çözümünüzü  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a>1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve izlemeyi etkinleştirme  
 Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacak ve değiştirme *Web.config* izlemeyi etkinleştirmek için dosya.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın ve tıklatın **dosya**, **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** penceresinde tıklatın **ASP.NET Web Forms uygulaması**.  
  
3.  İçinde **adı**, girin `TestApp` ve basın **Tamam**.  
  
4.  Sağ **TestApp** altında proje **Çözüm Gezgini**seçeneğini belirleyip **kimlik ve erişim**.  
  
5.  **Kimlik ve erişim** penceresi görüntülenir. Altında **sağlayıcıları**seçin **yerel geliştirme STS ile uygulamanızı Test**, ardından **Uygula**.  
  
6.  Yeni bir klasör oluşturun, adlı **günlükleri** kök **C:** gibi sürücü gösterilen: **C:\logs**  
  
7.  Aşağıdakileri ekleyin  **\<system.diagnostics >** öğesine *Web.config* hemen kapanış aşağıdaki yapılandırma dosyası  **\</configSections >** öğesi gibi gösterilir:  
  
    ```xml  
    <configuration>  
        <configSections>  
        …  
        </configSections>  
        <system.diagnostics>  
            <sources>  
                <source name="System.IdentityModel" switchValue="Verbose">  
                    <listeners>  
                        <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="C:\logs\WIF.xml" />  
                    </listeners>  
                </source>  
            </sources>  
            <trace autoflush="true" />  
        </system.diagnostics>  
    ```  
  
    > [!NOTE]
    >  Belirtilen dizin konumu **initializeData** günlüğü başlamadan önce özniteliği bulunması gerekir. Günlük konumu mevcut değilse oluşturulur.  
  
     Yukarıdaki yapılandırma ayarlarını etkinleştirir **ayrıntılı** WIF için izleme ve sonuçta elde edilen günlüğe kaydetme **C:logsWIF.xml** dosya.  
  
## <a name="step-2--test-your-solution"></a>2. adım – çözümünüzü  
 Bu adımda, günlükleri kayıtlı olduğunu doğrulamak için WIF etkinleştirilmiş ASP.NET uygulamanızı test.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a>Başarılı izleme için ASP.NET WIF özellikli uygulamanızı test etmek için  
  
1.  Tuşlarına basarak çözümü çalıştırın **F5** anahtarı. Varsayılan ASP.NET giriş sayfası ile sunulan ve gerekir otomatik olarak kullanıcı adıyla kimlik doğrulaması *Terry*, geliştirme STS tarafından döndürülen varsayılan kullanıcı olduğu.  
  
2.  Tarayıcı penceresini kapatın ve ardından gidin **C:\logs** klasör. Açık **C:\logs\WIF.xml** bir metin düzenleyicisi kullanarak dosya.  
  
3.  İnceleme **WIF.xml** dosya ve başlayarak girişleri içerdiğini doğrulayın  **\<E2ETraceEvent >**. Bu izlemeler içerecek  **\<TraceRecord >** izlenen etkinliğinin açıklamalarını öğeleri gibi **doğrulama SecurityToken**.
