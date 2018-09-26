---
title: 'Nasıl yapılır: WIF izlemeyi etkinleştirme'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: f763c279c29bec73d4fc20d59dc86726d84e21bd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47207120"
---
# <a name="how-to-enable-wif-tracing"></a>Nasıl yapılır: WIF izlemeyi etkinleştirme
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu nasıl yapılır, bir ASP.NET uygulamasında WIF izlemeyi etkinleştirmek için adım adım ayrıntılı yordamları sağlar. Ayrıca İzleme dinleyicisi doğrulamak için uygulamayı test etme yönergeleri sağlar ve günlük düzgün çalışıyor. Bu 'Nasıl Yapılır' konusunda bir Güvenlik Belirteci Hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bunun yerine Kimlik ve Erişim aracı ile birlikte gelen Geliştirme STS'si kullanılır. Geliştirme STS'si gerçek kimlik doğrulaması yapmaz ve yalnızca test amaçlarına yöneliktir. Bu 'Nasıl Yapılır' konusunu tamamlamak için Kimlik ve Erişim aracını yüklemeniz gerekir. Şu konumdan indirilebilir: [kimlik ve erişim aracı](https://go.microsoft.com/fwlink/?LinkID=245849)  
  
> [!IMPORTANT]
>  Pasif uygulamalar için WIF izlemeyi etkinleştirme, diğer bir deyişle, WS-Federasyon protokolünü kullanan uygulamalar potansiyel olarak kullanıma kötü amaçlı bir taraf uygulamaya hizmet (DoS) saldırısı reddi veya bilgilerin açıklanması. Bu, hem pasif RPs hem de edilgen STSes içerir. Bu nedenle, WIF izleme edilgen RPs veya STSes bir üretim ortamında etkinleştirmenizi değil öneririz.  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Genel Bakış  
  
-   Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve izlemeyi etkinleştirme  
  
-   2. adım – çözümünüzü test etme  
  
## <a name="objectives"></a>Amaçlar  
  
-   WIF ve kimlik ve erişim aracı geliştirme STS'sini kullanan basit bir ASP.NET uygulaması oluşturma  
  
-   İzlemeyi etkinleştirme ve çalışır durumda olduğunu doğrulayın  
  
## <a name="overview"></a>Genel Bakış  
 İzleme, hata ayıklama ve birçok tür belirteçleri, tanımlama bilgileri, talep, protokol iletileri ve daha da dahil olmak üzere, WIF ile ilgili sorunları gidermeye sağlar. WIF izleme WCF izleme benzer. Örneğin, kritik iletileri kadar her şey için tüm iletileri görüntülemek için izlemeleri ayrıntı seçebilirsiniz. WIF izlemeleri oluşturulabilir **.xml** dosyaları veya **.svclog** hizmet izleme Görüntüleyicisi aracı kullanarak görüntülenebilen olan dosyaları. Bu araç bulunan **bin** Windows SDK yükleme dizini yolu bilgisayarınızda, örneğin: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve izlemeyi etkinleştirme  
  
-   2. adım – çözümünüzü test etme  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a>1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve izlemeyi etkinleştirme  
 Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacak ve değiştirme *Web.config* izlemeyi etkinleştirmek için dosya.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın ve tıklayın **dosya**, **yeni**, ardından **proje**.  
  
2.  İçinde **yeni proje** penceresinde tıklayın **ASP.NET Web Forms uygulaması**.  
  
3.  İçinde **adı**, girin `TestApp` basın **Tamam**.  
  
4.  Sağ **TestApp** altındaki proje **Çözüm Gezgini**, ardından **kimlik ve erişim**.  
  
5.  **Kimlik ve erişim** penceresi görüntülenir. Altında **sağlayıcıları**seçin **uygulamanızı yerel geliştirme STS'si ile Test**, ardından **Uygula**.  
  
6.  Yeni bir klasör oluşturun, adlı **günlükleri** kökünde **C:** gibi sürücü gösterilen: **C:\logs**  
  
7.  Aşağıdaki  **\<system.diagnostics >** öğesine *Web.config* kapatma takip yapılandırma dosyası  **\</configSections >** öğesi gibi gösterilir:  
  
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
    >  Belirtilen dizin konumunu **initializeData** günlük başlamadan önce özniteliği bulunmalıdır. Günlük konumu mevcut değilse oluşturulur.  
  
     Yukarıdaki yapılandırma ayarlarını etkinleştirir **ayrıntılı** için WIF izleme ve sonuçta elde edilen günlüğe kaydetme **C:logsWIF.xml** dosya.  
  
## <a name="step-2--test-your-solution"></a>2. adım – çözümünüzü test etme  
 Bu adımda, WIF özelliği etkinleştirilmiş ASP.NET uygulamanızı günlükleri kaydı doğrulamak için test eder.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a>Başarılı izleme için ASP.NET WIF özelliği etkinleştirilmiş uygulamanızı test etmek için  
  
1.  Tuşlarına basarak çözümü çalıştırın **F5** anahtarı. Verilecek varsayılan ASP.NET ana sayfası gösterilir ve otomatik olarak kullanıcı adıyla kimlik doğrulaması *Terry*, geliştirme STS tarafından döndürülen varsayılan kullanıcı olduğu.  
  
2.  Tarayıcı penceresini kapatın ve ardından gidin **C:\logs** klasör. Açık **C:\logs\WIF.xml** bir metin düzenleyicisi kullanarak dosya.  
  
3.  İnceleme **WIF.xml** ile başlayan girişler içerdiğini doğrulayın ve dosya  **\<E2ETraceEvent >**. Bu izlemeler içerecek  **\<TraceRecord >** açıklamaları izlenen etkinliğinin öğelerle gibi **doğrulama SecurityToken**.
