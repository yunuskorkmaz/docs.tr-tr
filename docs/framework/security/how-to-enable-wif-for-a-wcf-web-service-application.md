---
title: 'Nasıl yapılır: WCF Web hizmeti uygulaması için WIF etkinleştirme'
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 71897299d68c2f0e43def8e70730ea456d6e9e24
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46583986"
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a>Nasıl yapılır: WCF Web hizmeti uygulaması için WIF etkinleştirme
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Microsoft® Windows® Communication Foundation (WCF)  
  
## <a name="summary"></a>Özet  
 Bu 'Nasıl Yapılır' makalesi, bir WCF web hizmetinde WIF'yi etkinleştirmeye yönelik adım adım ayrıntılı yordamları sağlar. Ayrıca, uygulama çalıştırıldığında web hizmetinin beyanları doğru olarak sunduğunu doğrulamak amacıyla uygulamanın nasıl test edileceğine ilişkin yönergeler verilir. Bu 'Nasıl Yapılır' konusunda bir Güvenlik Belirteci Hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bunun yerine Kimlik ve Erişim aracı ile birlikte gelen Geliştirme STS'si kullanılır. Geliştirme STS'si gerçek kimlik doğrulaması yapmaz ve yalnızca test amaçlarına yöneliktir. Bu 'Nasıl Yapılır' konusunu tamamlamak için Kimlik ve Erişim aracını yüklemeniz gerekir. Şu konumdan indirilebilir: [kimlik ve erişim aracı](https://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Genel Bakış  
  
-   Adımların Özeti  
  
-   1. Adım – Basit bir WCF Hizmeti Oluşturma  
  
-   2. Adım – WCF Hizmeti İçin Bir İstemci Uygulaması Oluşturma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="objectives"></a>Amaçlar  
  
-   Verilen belirteçleri gerektiren bir WCF hizmeti oluşturma  
  
-   STS'den bir belirteç isteyen ve bunu WCF hizmetine aktaran bir WCF istemcisi oluşturma  
  
## <a name="overview"></a>Genel Bakış  
 Bu 'Nasıl Yapılır' makalesi, bir geliştiricinin WCF hizmetleri geliştirirken federasyon kimlik doğrulamasını nasıl kullanabileceğini göstermeyi amaçlar. WCF hizmetlerinde federasyon kullanmanın avantajlarından bazıları şunlardır:  
  
1.  Kimlik doğrulamasını WCF hizmet kodunun dışında düzenleme  
  
2.  Varolan kimlik yönetimi çözümlerini yeniden kullanma  
  
3.  Diğer kimlik çözümleri ile birlikte çalışabilirlik  
  
4.  Esneklik ve gelecekteki değişikliklere uyum kolaylığı  
  
 WIF ve ilişkili Kimlik ve Erişim aracı, aşağıdaki adımlarda da gösterildiği üzere, federasyon kimlik doğrulamasını kullanarak WCF hizmeti geliştirmeyi ve test etmeyi kolaylaştırır.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. Adım – Basit bir WCF Hizmeti Oluşturma  
  
-   2. Adım – WCF Hizmeti İçin Bir İstemci Uygulaması Oluşturma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="step-1--create-a-simple-wcf-service"></a>1. Adım – Basit bir WCF Hizmeti Oluşturma  
 Bu adımda, Kimlik ve Erişim aracının içindeki Geliştirme STS'sini kullanan yeni bir WCF hizmeti oluşturacaksınız.  
  
#### <a name="to-create-a-simple-wcf-service"></a>Basit bir WCF hizmeti oluşturmak için  
  
1.  Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.  
  
2.  Visual Studio'da **dosya**, tıklayın **yeni**ve ardından **proje**.  
  
3.  İçinde **yeni proje** penceresinde tıklayın **WCF hizmeti uygulaması**.  
  
4.  İçinde **adı**, girin `TestService` basın **Tamam**.  
  
5.  Sağ **TestService** altındaki proje **Çözüm Gezgini**, ardından **kimlik ve erişim**.  
  
6.  **Kimlik ve erişim** penceresi görüntülenir. Altında **sağlayıcıları**seçin **uygulamanızı yerel geliştirme STS'si ile Test**, ardından **Uygula**. Kimlik ve erişim aracı, hizmeti WIF kullanacak ve kimlik doğrulaması için yerel geliştirme sts'sine yapılandırır (**LocalSTS**) yapılandırma öğelerine ekleyerek *Web.config* dosya.  
  
7.  İçinde *gt;service1.svc.cs* ekleyin bir `using` yönergesi **System.Security.Claims** ad alanı ve varolan kodu şu kodla değiştirip dosyayı kaydedin:  
  
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
  
     `ComputeResponse` Yöntemi tarafından verilen çeşitli beyanların özelliklerini görüntüler **LocalSTS**.  
  
8.  İçinde *Iservice1.cs* dosya, var olan kodu aşağıdakiyle değiştirin ve ardından dosyayı kaydedin:  
  
    ```csharp  
    [ServiceContract]  
    public interface IService1  
    {  
        [OperationContract]  
        string ComputeResponse(string input);  
    }  
    ```  
  
9. Projeyi oluşturun.  
  
10. Tuşuna **Ctrl-F5** hata ayıklayıcıyı başlatmadan hizmeti çalıştırmak için. Hizmet için bir Web sayfası açmak ve doğrulayabilirsiniz **LocalSTS** bildirim alanında (sistem tepsisi) bakarak çalışıyor.  
  
    > [!IMPORTANT]
    >  Her ikisi de **TestService** ve **LocalSTS** sonraki adımda istemci uygulamasına hizmet başvurusunu eklediğinizde, çalışıyor olması gerekir.  
  
## <a name="step-2--create-a-client-application-for-the-wcf-service"></a>2. Adım – WCF Hizmeti İçin Bir İstemci Uygulaması Oluşturma  
 Bu adımda, önceki adımda oluşturduğunuz WCF hizmeti ile kimlik doğrulamak için Geliştirme STS'sini kullanan bir konsol uygulaması oluşturacaksınız.  
  
#### <a name="to-create-a-client-application"></a>İstemci uygulaması oluşturmak için  
  
1.  Visual Studio'da çözüme sağ tıklayın, **Ekle**ve ardından **yeni proje**.  
  
2.  İçinde **Yeni Proje Ekle** penceresinde **konsol uygulaması** gelen **Visual C#** şablonları listesinde, girin `Client`ve tuşuna **Tamam**. Yeni proje, çözüm klasörünüzde oluşturulur.  
  
3.  Sağ **başvuruları** altında **istemci** proje ve ardından **hizmet Başvurusu Ekle**.  
  
4.  İçinde **hizmet Başvurusu Ekle** penceresinde, aşağı açılan oka tıklayın **bulma** düğmesini tıklatın ve tıklatın **çözüm içerisindeki Hizmetler**. **Adresi** daha önce oluşturduğunuz WCF Hizmeti ile otomatik olarak doldurulur ve **Namespace** ayarlanacak **ServiceReference1**. **Tamam**'ı tıklatın.  
  
    > [!IMPORTANT]
    >  Her ikisi de **TestService** ve **LocalSTS** istemciye hizmet başvurusunu eklediğinizde, çalışıyor olması gerekir.  
  
5.  Visual Studio, WCF hizmeti için proxy sınıfları üretecek ve gerekli tüm başvuru bilgilerini ekleyecektir. Öğeleri ekleyecektir *App.config* hizmeti ile kimlik doğrulaması STS gelen bir belirteç alacak şekilde istemciyi yapılandırmak için bir dosya. Bu işlem tamamlandığında **Program.cs** dosyası açılır. Ekleme bir `using` yönergesi **System.ServiceModel** için başka bir **gt;Client.servicereference1**, değiştirin **ana** şu kod ile ardından yöntemi dosyayı kaydedin:  
  
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
  
6.  Açık *App.config* altına ilk alt öğe olarak aşağıdaki XML'i ekleyin ve dosya `<system.serviceModel>` öğesi, ardından dosyayı kaydedin:  
  
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
  
7.  Sağ **TestService** çözüm ve tıklayarak **başlangıç projelerini Ayarla**. **Başlangıç projesi** özellik sayfası açılır. İçinde **başlangıç projesi** özellik sayfasında, **birden fazla başlangıç projesi** tıklayın ardından **eylem** alan her bir proje ve seçin için **Başlat** aşağı açılan menüden. Tıklayın **Tamam** ayarları kaydetmek için.  
  
8.  Çözümü oluşturun.  
  
## <a name="step-3--test-your-solution"></a>3. Adım – Çözümünüzü Test Etme  
 Bu adımda, WIF özelliği etkinleştirilmiş WCF uygulamanızı test edecek ve beyanların sunulduğunu doğrulayacaksınız.  
  
#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a>WIF özelliği etkinleştirilmiş WCF uygulamanızı beyanlar açısından test etmek için  
  
1.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın. Bir konsol penceresi ve şu metnin sunulacaktır: **uygulamadan çıkmak içinse diğer herhangi bir tuşa hizmetini çağırmak için anahtar Enter tuşuna basın:**  
  
2.  Tuşuna **Enter**, ve konsolda şu beyan bilgilerinin görünmesi gerekir:  
  
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
    >  Her ikisi de **TestService** ve **LocalSTS** basmadan önce çalıştırmalıdır **Enter**. Hizmet için bir Web sayfası açmak ve doğrulayabilirsiniz **LocalSTS** bildirim alanında (sistem tepsisi) bakarak çalışıyor.  
  
3.  Bu beyanlar konsolda görünüyorsa, WCF hizmetinden beyanları görüntülemek üzere STS ile başarılı bir şekilde kimlik doğrulamışsınız demektir.
