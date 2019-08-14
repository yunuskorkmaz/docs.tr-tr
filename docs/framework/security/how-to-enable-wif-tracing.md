---
title: 'Nasıl yapılır: WIF İzlemeyi Etkinleştirme'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: 40349c5aac7634a515b40a9cc1ab5e75492600c4
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971514"
---
# <a name="how-to-enable-wif-tracing"></a>Nasıl yapılır: WIF İzlemeyi Etkinleştirme

## <a name="applies-to"></a>Uygulanan Öğe

- Microsoft® Windows® Identity Foundation (WIF)

- ASP.NET® Web Forms

## <a name="summary"></a>Özet

Bu nasıl yapılır, bir ASP.NET uygulamasında WıF izlemeyi etkinleştirmek için ayrıntılı adım adım yordamlar sağlar. Ayrıca, İzleme dinleyicisinin ve günlüğün düzgün çalıştığını doğrulamak üzere uygulamayı test eden yönergeler de sağlar. Bu 'Nasıl Yapılır' konusunda bir Güvenlik Belirteci Hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bunun yerine Kimlik ve Erişim aracı ile birlikte gelen Geliştirme STS'si kullanılır. Geliştirme STS'si gerçek kimlik doğrulaması yapmaz ve yalnızca test amaçlarına yöneliktir. Bu 'Nasıl Yapılır' konusunu tamamlamak için Kimlik ve Erişim aracını yüklemeniz gerekir. Bu, aşağıdaki konumdan indirilebilir: [Kimlik ve erişim aracı](https://go.microsoft.com/fwlink/?LinkID=245849)

> [!IMPORTANT]
> Pasif uygulamalar için WıF izlemeyi etkinleştirmek, diğer bir deyişle, WS-Federation protokolünü kullanan uygulamalar, uygulamayı hizmet reddi (DoS) saldırılarına veya kötü amaçlı bir tarafa yönelik bilgilerin açığa çıkmasına neden olabilir. Bu, hem pasif RPs hem de pasif stler içerir. Bu nedenle, bir üretim ortamında pasif RPs veya stler için WıF izlemeyi etkinleştirmenizi öneririz.

## <a name="contents"></a>İçindekiler

- Amaçlar

- Genel Bakış

- Adımların Özeti

- 1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve Izlemeyi etkinleştirme

- 2\. Adım – Çözümünüzü test etme

## <a name="objectives"></a>Amaçlar

- Kimlik ve erişim aracından WıF ve geliştirme STS 'sini kullanan basit bir ASP.NET uygulaması oluşturma

- İzlemeyi etkinleştirme ve çalıştığını doğrulama

## <a name="overview"></a>Genel Bakış

İzleme, belirteçler, tanımlama bilgileri, talepler, protokol iletileri ve daha fazlası dahil olmak üzere WıF ile ilgili birçok tür sorunu ayıklamanıza ve gidermenize olanak sağlar. WıF izleme, WCF izlemeye benzerdir; Örneğin, kritik iletilerden tüm iletilere her şeyi görüntüleyen izlemelerin ayrıntı düzeyini seçebilirsiniz. WıF izlemeleri **. xml** dosyalarında veya hizmet Izleme Görüntüleyicisi Aracı kullanılarak görüntülenebilen **. svclog** dosyalarında oluşturulabilir. Bu araç, bilgisayarınızdaki Windows SDK yüklemesi yolunun **bin** dizininde bulunur, örneğin: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.

## <a name="summary-of-steps"></a>Adımların Özeti

- 1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve Izlemeyi etkinleştirme

- 2\. Adım – Çözümünüzü test etme

## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a>1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve Izlemeyi etkinleştirme

Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacak ve izlemeyi etkinleştirmek için *Web. config* dosyasını değiştirecaksınız.

### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için

1. Visual Studio 'Yu başlatın ve **Dosya**, **Yeni**ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** penceresinde, **ASP.NET Web Forms uygulama**' ya tıklayın.

3. **Ad**alanına girin `TestApp` ve **Tamam**' a basın.

4. **Çözüm Gezgini**altında **TestApp** projesine sağ tıklayın **ve ardından kimlik ve erişim**' i seçin.

5. **Kimlik ve erişim** penceresi görüntülenir. **Sağlayıcılar**bölümünde, **yerel geliştirme sts 'Si Ile uygulamanızı test et**' i seçin ve **Uygula**' ya tıklayın.

6. **C:** sürücüsünün kökündeki adlandırılmış **günlüklerde** aşağıda gösterildiği gibi yeni bir klasör oluşturun: **C:\logs.**

7. Aşağıda gösterildiği gibi,  **Kapanış\</configSections >** öğesinin hemen ardından *Web. config* yapılandırma dosyasına aşağıdaki  **\<System. Diagnostics >** öğesini ekleyin:

    ```xml
    <configuration>
        <configSections>
            ...
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
    > Günlük kaydı başlamadan önce **ınitializedata** özniteliğinde belirtilen dizin konumu mevcut olmalıdır. Konum yoksa, hiçbir günlük oluşturulmaz.

     Yukarıdaki yapılandırma ayarları WıF için **ayrıntılı** izlemeyi etkinleştirir ve elde edilen günlüğü **C:logswif.xml** dosyasına kaydeder.

## <a name="step-2--test-your-solution"></a>2\. Adım – Çözümünüzü test etme

Bu adımda, günlüklerin kaydedildiğini doğrulamak üzere WıF özellikli ASP.NET uygulamanızı test edersiniz.

### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a>WıF özellikli ASP.NET uygulamanızı başarıyla izleme için sınamak için

1. **F5** tuşuna basarak çözümü çalıştırın. Varsayılan ASP.NET ana sayfası ve geliştirme STS tarafından döndürülen varsayılan kullanıcı olan *Terry*adlı Kullanıcı adı ile otomatik olarak kimlik doğrulaması yapmanız gerekir.

2. Tarayıcı penceresini kapatın ve **C:\logs** klasörüne gidin. Bir metin düzenleyicisi kullanarak **C:\logs\wif.xml** dosyasını açın.

3. **WIF. xml** dosyasını inceleyin ve  **\<E2ETraceEvent >** ile başlayan girdileri içerdiğini doğrulayın. Bu izlemeler, **SecurityToken doğrulaması**gibi izlenen etkinliğin açıklamalarını içeren izleme  **\<ecord >** öğelerini içerir.
