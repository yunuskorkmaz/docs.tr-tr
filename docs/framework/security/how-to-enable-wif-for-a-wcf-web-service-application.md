---
title: 'Nasıl yapılır: WCF Web Hizmeti Uygulaması için WIF Etkinleştirme'
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
ms.openlocfilehash: b9fa1f815a962adc0b3c91177021788734b92bb6
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041451"
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a>Nasıl yapılır: WCF Web Hizmeti Uygulaması için WIF Etkinleştirme
## <a name="applies-to"></a>Uygulanan Öğe

- Microsoft® Windows® Identity Foundation (WIF)

- Microsoft® Windows® Communication Foundation (WCF)

## <a name="summary"></a>Özet

Bu 'Nasıl Yapılır' makalesi, bir WCF web hizmetinde WIF'yi etkinleştirmeye yönelik adım adım ayrıntılı yordamları sağlar. Ayrıca, uygulama çalıştırıldığında web hizmetinin beyanları doğru olarak sunduğunu doğrulamak amacıyla uygulamanın nasıl test edileceğine ilişkin yönergeler verilir. Bu 'Nasıl Yapılır' konusunda bir Güvenlik Belirteci Hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bunun yerine Kimlik ve Erişim aracı ile birlikte gelen Geliştirme STS'si kullanılır. Geliştirme STS'si gerçek kimlik doğrulaması yapmaz ve yalnızca test amaçlarına yöneliktir. Bu 'Nasıl Yapılır' konusunu tamamlamak için Kimlik ve Erişim aracını yüklemeniz gerekir. Bu, aşağıdaki konumdan indirilebilir: [Kimlik ve erişim aracı](https://go.microsoft.com/fwlink/?LinkID=245849)

## <a name="contents"></a>İçindekiler

- Amaçlar

- Genel Bakış

- Adımların Özeti

- 1\. Adım – Basit bir WCF Hizmeti Oluşturma

- 2\. Adım – WCF Hizmeti İçin Bir İstemci Uygulaması Oluşturma

- 3\. Adım – Çözümünüzü Test Etme

## <a name="objectives"></a>Amaçlar

- Verilen belirteçleri gerektiren bir WCF hizmeti oluşturma

- STS'den bir belirteç isteyen ve bunu WCF hizmetine aktaran bir WCF istemcisi oluşturma

## <a name="overview"></a>Genel Bakış

Bu 'Nasıl Yapılır' makalesi, bir geliştiricinin WCF hizmetleri geliştirirken federasyon kimlik doğrulamasını nasıl kullanabileceğini göstermeyi amaçlar. WCF hizmetlerinde federasyon kullanmanın avantajlarından bazıları şunlardır:

1. Kimlik doğrulamasını WCF hizmet kodunun dışında düzenleme

2. Varolan kimlik yönetimi çözümlerini yeniden kullanma

3. Diğer kimlik çözümleri ile birlikte çalışabilirlik

4. Esneklik ve gelecekteki değişikliklere uyum kolaylığı

WIF ve ilişkili Kimlik ve Erişim aracı, aşağıdaki adımlarda da gösterildiği üzere, federasyon kimlik doğrulamasını kullanarak WCF hizmeti geliştirmeyi ve test etmeyi kolaylaştırır.

## <a name="summary-of-steps"></a>Adımların Özeti

- 1\. Adım – Basit bir WCF Hizmeti Oluşturma

- 2\. Adım – WCF Hizmeti İçin Bir İstemci Uygulaması Oluşturma

- 3\. Adım – Çözümünüzü Test Etme

## <a name="step-1--create-a-simple-wcf-service"></a>1\. Adım – Basit bir WCF Hizmeti Oluşturma

Bu adımda, Kimlik ve Erişim aracının içindeki Geliştirme STS'sini kullanan yeni bir WCF hizmeti oluşturacaksınız.

#### <a name="to-create-a-simple-wcf-service"></a>Basit bir WCF hizmeti oluşturmak için

1. Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.

2. Visual Studio 'da **Dosya**' ya, **Yeni**' ye ve ardından **Proje**' ye tıklayın.

3. **Yeni proje** penceresinde, **WCF hizmeti uygulaması**' na tıklayın.

4. **Ad**alanına girin `TestService` ve **Tamam**' a basın.

5. **Çözüm Gezgini**altında **TestService** projesine sağ tıklayın **ve ardından kimlik ve erişim**' i seçin.

6. **Kimlik ve erişim** penceresi görüntülenir. **Sağlayıcılar**bölümünde, **yerel geliştirme sts 'Si Ile uygulamanızı test et**' i seçin ve **Uygula**' ya tıklayın. Kimlik ve erişim aracı, *Web. config* dosyasına yapılandırma öğeleri ekleyerek, hizmeti WIF ve yerel geliştirme sts 'ye (**LocalSTS**) dış kimlik doğrulaması yapmak üzere yapılandırır.

7. *Service1.svc.cs* dosyasında, `using` **System. Security. Claim** ad alanı için bir yönerge ekleyin ve mevcut kodu aşağıdaki kodla değiştirin, ardından dosyayı kaydedin:

    ```csharp
    public class Service1 : IService1
    {
        public string ComputeResponse(string input)
        {
            // Get the caller's identity from ClaimsPrincipal.Current
            ClaimsPrincipal claimsPrincipal = OperationContext.Current.ClaimsPrincipal;

            // Start generating the output
            StringBuilder builder = new StringBuilder();
            builder.AppendLine("Computed by ClaimsAwareWebService");
            builder.AppendLine("Input received from client:" + input);

            if (claimsPrincipal != null)
            {
                // Display the claims from the caller. Do not use this code in a production application.
                ClaimsIdentity identity = claimsPrincipal.Identity as ClaimsIdentity;
                builder.AppendLine("Client Name:" + identity.Name);
                builder.AppendLine("IsAuthenticated:" + identity.IsAuthenticated);
                builder.AppendLine("The service received the following issued claims of the client:");

                // Iterate over the caller’s claims and append to the output
                foreach (Claim claim in claimsPrincipal.Claims)
                {
                    builder.AppendLine("ClaimType :" + claim.Type + "   ClaimValue:" + claim.Value);
                }
            }

            return builder.ToString();
        }
    }
    ```

    Yöntemi `ComputeResponse` , **LocalSTS**tarafından verilen çeşitli taleplerin özelliklerini görüntüler.

8. *IService1.cs* dosyasında, var olan kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:

    ```csharp
    [ServiceContract]
    public interface IService1
    {
        [OperationContract]
        string ComputeResponse(string input);
    }
    ```

9. Projeyi oluşturun.

10. Hata ayıklayıcıyı başlatmadan hizmeti çalıştırmak için **CTRL-F5** tuşlarına basın. Hizmet için bir Web sayfası açık olmalıdır ve bildirim alanına (sistem tepsisi) bakarak **LocalSTS** 'nin çalıştığını doğrulayabilirsiniz.

    > [!IMPORTANT]
    > Bir sonraki adımda istemci uygulamasına hizmet başvurusunu eklediğinizde hem **TestService** hem de **LocalSTS** çalışıyor olmalıdır.

## <a name="step-2--create-a-client-application-for-the-wcf-service"></a>2\. Adım – WCF Hizmeti İçin Bir İstemci Uygulaması Oluşturma

Bu adımda, önceki adımda oluşturduğunuz WCF hizmeti ile kimlik doğrulamak için Geliştirme STS'sini kullanan bir konsol uygulaması oluşturacaksınız.

#### <a name="to-create-a-client-application"></a>İstemci uygulaması oluşturmak için

1. Visual Studio 'da çözüme sağ tıklayın, **Ekle**' ye tıklayın ve ardından **Yeni proje**' ye tıklayın.

2. **Yeni Proje Ekle** penceresinde,  **C# görsel** şablonlar listesinden **konsol uygulaması** ' nı seçin, yazın `Client`ve ardından **Tamam**' a basın. Yeni proje, çözüm klasörünüzde oluşturulur.

3. **İstemci** projesi altındaki **Başvurular** ' a sağ tıklayın ve ardından **hizmet başvurusu Ekle**' ye tıklayın.

4. **Hizmet başvurusu Ekle** penceresinde **bul** düğmesinin yanındaki açılan oka tıklayın ve **çözümdeki hizmetler**' e tıklayın. **Adres** , daha önce oluşturduğunuz WCF hizmeti ile otomatik olarak doldurulur ve **ad alanı** **ServiceReference1**olarak ayarlanır. **Tamam**'ı tıklatın.

    > [!IMPORTANT]
    > İstemciye hizmet başvurusunu eklediğinizde hem **TestService** hem de **LocalSTS** çalışıyor olmalıdır.

5. Visual Studio, WCF hizmeti için proxy sınıfları üretecek ve gerekli tüm başvuru bilgilerini ekleyecektir. Ayrıca, istemciyi hizmette kimlik doğrulaması yapmak üzere STS 'den bir belirteç alacak şekilde yapılandırmak için *app. config* dosyasına öğe ekler. Bu işlem tamamlandığında, **program.cs** dosyası açılır. `using` **System. ServiceModel** ve **Client. ServiceReference1**için bir yönerge ekleyin, **Main** metodunu aşağıdaki kodla değiştirin, sonra dosyayı kaydedin:

    ```csharp
    static void Main(string[] args)
    {
        // Create the client for the service
        Service1Client client = new Service1Client();
        Console.WriteLine("-------------WCF Client Application--------------\n");

        while (!ShouldQuitApplication())
        {
            try
            {
                Console.WriteLine(client.ComputeResponse("Hello World"));
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
                Console.WriteLine(e.StackTrace);
                Exception ex = e.InnerException;
                while (ex != null)
                {
                    Console.WriteLine("===========================");
                    Console.WriteLine(ex.Message);
                    Console.WriteLine(ex.StackTrace);
                    ex = ex.InnerException;
                }
            }
            catch (TimeoutException)
            {
                Console.WriteLine("Timed out...");
            }
            catch (Exception e)
            {
                Console.WriteLine("An unexpected exception occurred.");
                Console.WriteLine(e.StackTrace);
            }
        }

        client.Close();

        if (client != null)
        {
            client.Abort();
        }
    }

    static bool ShouldQuitApplication()
    {
        Console.WriteLine("---------------------------------------------------------------------");
        Console.WriteLine("Press Enter key to invoke service, any other key to quit application:");
        Console.WriteLine("----------------------------------------------------------------------");

        ConsoleKeyInfo keyInfo = Console.ReadKey();
        if (keyInfo.Key == ConsoleKey.Enter)
            return false;
        return true;
    }
    ```

6. *App. config* dosyasını açın ve aşağıdaki XML `<system.serviceModel>` öğesini öğesinin altındaki ilk alt öğe olarak ekleyin, sonra dosyayı kaydedin:

    ```xml
    <behaviors>
       <endpointBehaviors>
         <behavior>
           <clientCredentials>
             <serviceCertificate>
               <authentication certificateValidationMode="None"/>
             </serviceCertificate>
           </clientCredentials>
         </behavior>
       </endpointBehaviors>
     </behaviors>
    ```

    Bu, sertifika doğrulamayı devre dışı bırakır.

7. **TestService** çözümüne sağ tıklayın ve **Başlangıç projelerini ayarla**' ya tıklayın. **Başlangıç projesi** Özellik sayfası açılır. **Başlangıç projesi** Özellik sayfasında, **birden fazla başlangıç** projesi ' ni seçin ve ardından her proje için **eylem** alanına tıklayın ve açılan menüden **Başlat** ' ı seçin. Ayarları kaydetmek için **Tamam** ' ı tıklatın.

8. Çözümü oluşturun.

## <a name="step-3--test-your-solution"></a>3\. Adım – Çözümünüzü Test Etme

Bu adımda, WIF özelliği etkinleştirilmiş WCF uygulamanızı test edecek ve beyanların sunulduğunu doğrulayacaksınız.

#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a>WIF özelliği etkinleştirilmiş WCF uygulamanızı beyanlar açısından test etmek için

1. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın. Bir konsol penceresi ve aşağıdaki metinle birlikte sunulmalısınız: **Hizmeti çağırmak için ENTER tuşuna basın, uygulamadan çıkmak için başka herhangi bir anahtar:**

2. **ENTER**tuşuna basın ve aşağıdaki talep bilgilerinin konsolunda görünmesi gerekir:

    ```
    Computed by Service1
    Input received from client: Hello World
    Client Name: Terry
    IsAuthenticated: True
    The service received the following issued claims of the client:
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name    ClaimValue:Terry
    ClaimType :http://schema.xmlsoap.org/ws/2005/05/identity/claims/surname    ClaimValue:Adams
    ClaimType :http://schemas.microsoft.com/ws/2008/06/identity/claims/role    ClaimValue:developer
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress    ClaimValue:terry@contoso.com
    ```

    > [!IMPORTANT]
    > **ENTER**tuşuna basarak, hem **TestService** hem de **LocalSTS** çalışıyor olmalıdır. Hizmet için bir Web sayfası açık olmalıdır ve bildirim alanına (sistem tepsisi) bakarak **LocalSTS** 'nin çalıştığını doğrulayabilirsiniz.

3. Bu beyanlar konsolda görünüyorsa, WCF hizmetinden beyanları görüntülemek üzere STS ile başarılı bir şekilde kimlik doğrulamışsınız demektir.
