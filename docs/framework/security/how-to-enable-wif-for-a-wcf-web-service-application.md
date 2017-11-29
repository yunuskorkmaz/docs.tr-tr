---
title: "Nasıl yapılır: Bir WCF Web hizmeti uygulaması WIF etkinleştir"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 7db69de994770e122dd4a4233b9a44d572c32344
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a>Nasıl yapılır: Bir WCF Web hizmeti uygulaması WIF etkinleştir
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Microsoft® Windows® Communication Foundation (WCF)  
  
## <a name="summary"></a>Özet  
 Bu 'Nasıl Yapılır' makalesi, bir WCF web hizmetinde WIF'yi etkinleştirmeye yönelik adım adım ayrıntılı yordamları sağlar. Ayrıca, uygulama çalıştırıldığında web hizmetinin beyanları doğru olarak sunduğunu doğrulamak amacıyla uygulamanın nasıl test edileceğine ilişkin yönergeler verilir. Bu 'Nasıl Yapılır' konusunda bir Güvenlik Belirteci Hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bunun yerine Kimlik ve Erişim aracı ile birlikte gelen Geliştirme STS'si kullanılır. Geliştirme STS'si gerçek kimlik doğrulaması yapmaz ve yalnızca test amaçlarına yöneliktir. Bu 'Nasıl Yapılır' konusunu tamamlamak için Kimlik ve Erişim aracını yüklemeniz gerekir. Şu konumdan indirilebilir: [kimlik ve erişim aracı](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
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
  
2.  Visual Studio'da sırasıyla **dosya**, tıklatın **yeni**ve ardından **proje**.  
  
3.  İçinde **yeni proje** penceresinde tıklatın **WCF hizmeti uygulaması**.  
  
4.  İçinde **adı**, girin `TestService` ve basın **Tamam**.  
  
5.  Sağ **TestService** altında proje **Çözüm Gezgini**seçeneğini belirleyip **kimlik ve erişim**.  
  
6.  **Kimlik ve erişim** penceresi görüntülenir. Altında **sağlayıcıları**seçin **yerel geliştirme STS ile uygulamanızı Test**, ardından **Uygula**. Kimlik ve erişim aracı yapılandırır WIF kullanan ve kimlik doğrulama STS yerel geliştirme için dış kaynak sağlamak için hizmet (**LocalSTS**) yapılandırma öğelerine ekleyerek *Web.config* dosya.  
  
7.  İçinde *Service1.svc.cs* dosya, ekleme bir `using` için yönerge **System.Security.Claims** ad alanı ve var olan kodu aşağıdaki ile değiştir ardından dosyayı kaydedin:  
  
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
  
     `ComputeResponse` Yöntemi tarafından verilen çeşitli talep özelliklerini görüntüler **LocalSTS**.  
  
8.  İçinde *IService1.cs* dosya, var olan kodu şununla değiştirin ve ardından dosyayı kaydedin:  
  
    ```csharp  
    [ServiceContract]  
    public interface IService1  
    {  
        [OperationContract]  
        string ComputeResponse(string input);  
    }  
    ```  
  
9. Projeyi oluşturun.  
  
10. Tuşuna **Ctrl-F5** hata ayıklayıcı başlatmadan hizmetini çalıştırmak için. Hizmet için bir Web sayfası açmanız ve olduğunu doğrulayabilirsiniz **LocalSTS** bildirim alanında (sistem tepsisi) bakarak çalışıyor.  
  
    > [!IMPORTANT]
    >  Her ikisi de **TestService** ve **LocalSTS** sonraki adımda istemci uygulaması için hizmet başvurusu eklediğinizde çalıştırıyor olması gerekir.  
  
## <a name="step-2--create-a-client-application-for-the-wcf-service"></a>2. Adım – WCF Hizmeti İçin Bir İstemci Uygulaması Oluşturma  
 Bu adımda, önceki adımda oluşturduğunuz WCF hizmeti ile kimlik doğrulamak için Geliştirme STS'sini kullanan bir konsol uygulaması oluşturacaksınız.  
  
#### <a name="to-create-a-client-application"></a>İstemci uygulaması oluşturmak için  
  
1.  Visual Studio'da çözüm üzerinde sağ tıklayın, **Ekle**ve ardından **yeni proje**.  
  
2.  İçinde **Yeni Proje Ekle** penceresinde, seçin **konsol uygulaması** gelen **Visual C#** şablonları listesinde, girin `Client`ve tuşuna basarak **Tamam**. Yeni proje, çözüm klasörünüzde oluşturulur.  
  
3.  Sağ **başvuruları** altında **istemci** proje ve ardından **hizmet Başvurusu Ekle**.  
  
4.  İçinde **hizmet Başvurusu Ekle** penceresinde, aşağı açılan oku tıklatın **bulma** düğmesini tıklatın ve tıklatın **çözüm Hizmetleri'nde**. **Adresi** daha önce oluşturduğunuz WCF Hizmeti ile otomatik olarak doldurulur ve **Namespace** ayarlanacak **ServiceReference1**. **Tamam**'ı tıklatın.  
  
    > [!IMPORTANT]
    >  Her ikisi de **TestService** ve **LocalSTS** istemciye hizmet başvurusu eklediğinizde çalıştırıyor olması gerekir.  
  
5.  Visual Studio, WCF hizmeti için proxy sınıfları üretecek ve gerekli tüm başvuru bilgilerini ekleyecektir. Öğelerine ekleyecek *App.config* STS hizmeti ile kimlik doğrulaması için gelen bir belirteç almak üzere istemciyi yapılandırmak için dosya. Bu işlem tamamlandığında **Program.cs** dosya açılır. Ekleme bir `using` için yönerge **System.ServiceModel** için başka bir **Client.ServiceReference1**, Değiştir **ana** aşağıdaki kod, ardından ile yöntemi dosyayı kaydedin:  
  
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
  
6.  Açık *App.config* dosya ve altında ilk alt öğesi olarak aşağıdaki XML eklemek `<system.serviceModel>` öğesi, ardından dosyayı kaydedin:  
  
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
  
7.  Sağ **TestService** çözümü ve tıklayarak **başlangıç projelerini Ayarla**. **Başlangıç projesi** özellik sayfası açılır. İçinde **başlangıç projesi** özellik sayfasında, **birden fazla başlangıç projesi** sonra'ı tıklatın **eylem** her proje ve select için alan **Başlat** açılır menüsünden. Tıklatın **Tamam** ayarları kaydetmek için.  
  
8.  Çözümü oluşturun.  
  
## <a name="step-3--test-your-solution"></a>3. Adım – Çözümünüzü Test Etme  
 Bu adımda, WIF özelliği etkinleştirilmiş WCF uygulamanızı test edecek ve beyanların sunulduğunu doğrulayacaksınız.  
  
#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a>WIF özelliği etkinleştirilmiş WCF uygulamanızı beyanlar açısından test etmek için  
  
1.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın. Bir konsol penceresi ve aşağıdaki metni sunulması gereken: **hizmeti, uygulama çıkmak için başka bir anahtar çağırmak için anahtar ENTER tuşuna basın:**  
  
2.  Tuşuna **Enter**, ve aşağıdaki talep bilgileri konsolunda görünecektir:  
  
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
    >  Her ikisi de **TestService** ve **LocalSTS** tuşuna önce çalıştırılması gerekir **Enter**. Hizmet için bir Web sayfası açmanız ve olduğunu doğrulayabilirsiniz **LocalSTS** bildirim alanında (sistem tepsisi) bakarak çalışıyor.  
  
3.  Bu beyanlar konsolda görünüyorsa, WCF hizmetinden beyanları görüntülemek üzere STS ile başarılı bir şekilde kimlik doğrulamışsınız demektir.
