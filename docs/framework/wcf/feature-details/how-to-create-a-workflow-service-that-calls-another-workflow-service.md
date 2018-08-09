---
title: 'Nasıl yapılır: Başka Bir İş Akışı Hizmetine Çağrı Yapan Bir İş Akışı Hizmeti Oluşturma'
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: fda5a7286c3d20c7cdc2093e58bfe3fbdcf1d1c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497197"
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a>Nasıl yapılır: Başka Bir İş Akışı Hizmetine Çağrı Yapan Bir İş Akışı Hizmeti Oluşturma
Başka bir iş akışı hizmetinden bilgi almak bir iş akışı hizmeti için bazen gereklidir.  Bu konuda, bir iş akışı hizmeti başka bir çağrı gösterilmektedir. Bu konuda, iki iş akışı hizmetleri oluşturacağız; bir giriş dizesi ilk hizmetin kullandığı dizesini ters kaydedildikten sonra büyük harfe dönüştürür giriş dizesi ve başka bir tersine çevirir bir yöntemi vardır.  
  
### <a name="to-create-the-reverser-workflow-service"></a>Reverser iş akışı hizmeti oluşturmak için  
  
1.  Çalıştırma [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yönetici olarak.  
  
2.  Seçin **dosya**, **yeni proje**. Altında **iş akışı** düğümünde **yüklü şablonlar** bölmesinde, **WCF iş akışı hizmeti uygulaması**. Çözüm adı `NestedServices` ve ardından **Tamam**.  
  
3.  Altında **sunucuları**, olduğundan emin olun **kullanım yerel IIS Web sunucusu** seçilir. Tıklatın **sanal dizini oluştur**. Tıklatın **Tamam** sanal dizinin başarıyla oluşturulduğunu belirten iletişim kutusu içinde.  
  
4.  Çözüm Gezgini'nde, yeniden adlandırmak için Service1.xamlx `StringReverserService.xamlx`.  
  
5.  Üzerinde **proje özelliklerini** sayfasında yeni proje için **Web** sekmesi. Ayarlama **eylemi Başlat** için **belirli sayfa**, StringReverserService.xamlx başlatmak için sayfa olarak seçin.  
  
6.  Tasarımcıda StringReverserService.xamlx açın ve varolan silin `ReceiveRequest` ve `SendReply` etkinlikleri ve ardından sürükleyin bir `ReceiveAndSendReply` mevcut dizisi etkinliğin etkinlik.  
  
    1.  Ayarlama **OperationName** ReverseString için.  
  
    2.  Ayarlama **ServiceContractName** IReverseString için.  
  
    3.  Seçin **CanCreateInstance** onay kutusu.  
  
7.  Seçin **SequentialService** etkinliği ve ardından **değişkenleri** Tasarımcısı'nın altındaki sekmesi. StringToReverse ve dize türünde ReversedStringToReturn adlı iki yeni değişken oluşturun.  
  
8.  Tıklatın **tanımla** bağlamak **alma** etkinlik. Tıklatın **parametreleri**ve StringToReverse için atar dize türünde InputString adlı bir parametre oluşturun.  
  
9. Tıklatın **tanımla** bağlamak **SendReplyToReceive** etkinlik. Tıklatın **parametreleri**ve ReversedStringToReturn için atanan dize türünde, ReversedString adlı bir parametre oluşturun.  
  
10. Hizmet mantığını uygulamak için StringLibrary adlı projeye yeni bir sınıf oluşturun.  Sınıf tanımını aşağıdaki kodla değiştirin.  
  
    ```  
    public class StringLibrary  
        {  
            public static String ReverseString(string StringToReverse)  
            {  
                char[] charArray = StringToReverse.ToCharArray();  
                Array.Reverse(charArray);  
                return new String(charArray);  
            }  
        }  
    ```  
  
11. Giriş, ReverseString yöntemini çağırmak için sürükleyin bir **InvokeMethod** araç etkinliğinden arasındaki boşluğu için **alma** ve **SendReply** etkinlikler. Etkinlik özelliklerini aşağıdaki gibi ayarlayın:  
  
    1.  **MethodName**: ReverseString  
  
    2.  **Sonuç**: ReversedStringToReturn  
  
    3.  **Parametreleri**: ile yeni bir parametre oluşturmak bir **yönü** , giriş, bir **türü** , dizenin ve **değeri** StringToReverse.  
  
    4.  **TargetType**: NestedServices.StringLibrary  
  
12. Hizmet, F5 tuşuna basarak sınayın. WCF Test görünen istemcisinde ReverseString() yöntemini çift tıklatın. İstek bölmesinde girin `Sample` InputString parametresinin değeri için. Tıklatın **çağırma**. Hizmeti, "elpmaS" döndürmelidir.  
  
### <a name="to-create-the-uppercaser-workflow-service"></a>UpperCaser iş akışı hizmeti oluşturmak için  
  
1.  NestedServices projesine sağ tıklatın ve **Ekle**, **yeni öğe**. İçinde **iş akışı** düğümü, select **WCF iş akışı hizmeti**ve yeni hizmet adı `UpperCaserService`. **Ekle**'yi tıklatın. Bu projeye UpperCaserService.xamlx adlı yeni bir iş akışı hizmeti eklemeniz gerekir.  
  
2.  Tasarımcıda UpperCaserService.xamlx açın ve varolan silin **ReceiveRequest** ve `SendReply` etkinlikleri ve sürükleme bir `ReceiveAndSendReply` mevcut dizisi etkinliğin etkinlik.  
  
    1.  Ayarlama **OperationName** UpperCaseString için.  
  
    2.  Ayarlama **ServiceContractName** IUpperCaseString için.  
  
    3.  Seçin **CanCreateInstance** onay kutusu.  
  
3.  SequentialService etkinliği seçin ve ardından **değişkenleri** Tasarımcısı'nın altındaki sekmesi. StringToUpper, StringToReverse ve dize türünde StringToReturn adlı üç yeni değişkenleri oluşturun.  
  
4.  Tıklatın **tanımla** bağlamak **alma** etkinlik. Tıklatın **parametreleri**ve StringToUpper için atar dize türünde InputString adlı bir parametre oluşturun.  
  
5.  Tıklatın **tanımla** bağlamak **SendReplyToReceive** etkinlik. Tıklatın **parametreleri**ve StringToReturn için atanan dize türünde, ModifiedString adlı bir parametre oluşturun.  
  
6.  Hizmet mantığını uygulamak için aşağıdaki kodu kullanarak StringLibrary sınıfında yeni bir yöntem oluşturun.  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
    ```  
  
7.  Giriş, UpperCaseString yöntemini çağırmak için sürükleyin bir **InvokeMethod** araç etkinliğinden arasındaki boşluğu için **alma** ve **SendReply** etkinlikler. Etkinlik özelliklerini aşağıdaki gibi ayarlayın:  
  
    1.  **MethodName**: UpperCaseString  
  
    2.  **Sonuç**: StringToReverse  
  
    3.  **Parametreleri**: ile yeni bir parametre oluşturmak bir **yönü** , giriş, bir **türü** , dizenin ve **değeri** StringToUpper.  
  
    4.  **TargetType**: NestedServices.StringLibrary  
  
8.  Artık ilk hizmet üzerinde değiştirilmiş dizesini arayacağız. Projeye sağ tıklayın ve seçin **hizmet Başvurusu Ekle**. Hizmeti için hizmet Başvurusu Ekle http://localhost/NestedServices/StringReverserService.xamlx ve ilk Web hizmetine erişmek için özel bir etkinlik oluşturmak için projeyi oluşturun.  
  
9. Yeni Etkinlik örneği arasında iş akışı sürükleyin **InvokeMethod** etkinlik ve **SendReplyToReceive** etkinlikler. Değişken StringToReverse yeni etkinliği ve değişken StringToReturn StringToReturn özelliğine InputString özelliğinin atayın.  
  
10. NestedServices projesi için Özellikler sayfasını açın ve değiştirme **belirli sayfa** içinde **Web** UpperCaserService.xamlx sekmesine.  
  
11. Hizmet, F5 tuşuna basarak sınayın. WCF Test görünen istemcisinde ReverseString() yöntemini çift tıklatın. İstek bölmesinde girin `Sample` InputString parametresinin değeri için. Tıklatın **çağırma**. Hizmeti, "ELPMAS" döndürmelidir.  
  
### <a name="to-create-a-client-to-call-the-services"></a>Hizmetleri çağırmak için bir istemci oluşturmak için  
  
1.  İstemci çözümü olarak adlandırılan yeni bir konsol uygulama projesi ekleyin.  
  
2.  İstemci projesine sağ tıklatın ve **hizmet Başvurusu Ekle**. Görüntülenen penceresinde **bulma**. StringReverserService.xamlx seçin ve ad alanı olarak ReverseService girin.  **Tamam**'ı tıklatın.  
  
3.  Program.cs içinde Main yöntemini aşağıdaki kodla değiştirin.  
  
    ```  
    static void Main(string[] args)  
    {  
        Console.Write("Input string to process:");  
        String input = Console.ReadLine();  
        var service = new ReverseService.ReverseStringClient();  
        Console.WriteLine("Output from service: {0}", service.ReverseString(input));  
        Console.ReadKey();  
    }  
    ```
