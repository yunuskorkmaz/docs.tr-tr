---
title: 'Nasıl yapılır: Başka Bir İş Akışı Hizmetine Çağrı Yapan Bir İş Akışı Hizmeti Oluşturma'
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: 1b30da34f7c85cccd98b18cd32b81c83630989b2
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258364"
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a>Nasıl yapılır: Başka Bir İş Akışı Hizmetine Çağrı Yapan Bir İş Akışı Hizmeti Oluşturma

Başka bir iş akışı hizmetinden bilgi almak bir iş akışı hizmeti için bazen gereklidir. Bu konu, başka bir iş akışı hizmeti çağırmak amacıyla gösterilmiştir. Bu konu başlığında, iki iş akışı hizmetleri oluşturacağız; bir Giriş dizesinin ilk hizmetin kullandığı dize ters sonra büyük harfe dönüştürür bir Giriş dizesinin ve başka bir tersine bir yöntemi vardır.

### <a name="to-create-the-reverser-workflow-service"></a>Reverser iş akışı hizmeti oluşturma

1.  Visual Studio'yu açın.

2.  Seçin **dosya** > **yeni proje**. Altında **iş akışı** düğümünde **yüklü şablonlar** bölmesinde **WCF iş akışı hizmeti uygulaması**. Çözüm adı `NestedServices` ve ardından **Tamam**.

3.  Altında **sunucuları**, emin **kullanım yerel IIS Web sunucusunda** seçilir. Tıklayın **sanal dizin oluşturma**. Tıklayın **Tamam** sanal dizinin başarıyla oluşturulduğunu belirten iletişim kutusu içinde.

4.  Çözüm Gezgini'nde, yeniden adlandırmak için Service1.xamlx `StringReverserService.xamlx`.

5.  Üzerinde **proje özellikleri** sayfasında yeni proje için **Web** sekmesi. Ayarlama **başlatma eylemi** için **belirli sayfa**, StringReverserService.xamlx başlatılacağı sayfa seçin.

6.  StringReverserService.xamlx Tasarımcısı'nda açın ve mevcut `ReceiveRequest` ve `SendReply` etkinlikleri daha sonra sürükleyin bir `ReceiveAndSendReply` mevcut sıralama etkinliğine etkinliğini.

    1.  Ayarlama **OperationName** ReverseString için.

    2.  Ayarlama **ServiceContractName** IReverseString için.

    3.  Seçin **CanCreateInstance** onay kutusu.

7.  Seçin **SequentialService** etkinlik ve ardından **değişkenleri** Tasarımcısı'nın altındaki sekmesi. StringToReverse ve dize türünde ReversedStringToReturn adlı iki yeni değişken oluşturun.

8.  Tıklayın **tanımla** bağlantısını **alma** etkinlik. Tıklayın **parametreleri**ve adlı InputString StringToReverse için atar String türünde bir parametre oluşturun.

9. Tıklayın **tanımla** bağlantısını **SendReplyToReceive** etkinlik. Tıklayın **parametreleri**ve ReversedString ReversedStringToReturn için atanan türü dize adlı bir parametre oluşturun.

10. Hizmet mantığını uygulamak için StringLibrary adlı projede yeni bir sınıf oluşturun.  Sınıf tanımını aşağıdaki kodla değiştirin.

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

11. Giriş ReverseString yöntemi çağırmak için sürükleyin bir **InvokeMethod** etkinliğini araç kutusundan arasındaki boşluk **alma** ve **SendReply** etkinlikler. Etkinlik özelliklerini şu şekilde ayarlayın:

    1.  **MethodName**: ReverseString

    2.  **Sonuç**: ReversedStringToReturn

    3.  **Parametreleri**: ile yeni parametre oluşturma bir **yönü** 'ın içinde bir **türü** dizesini ve **değer** StringToReverse.

    4.  **TargetType**: NestedServices.StringLibrary

12. F5 tuşuna basarak test hizmeti. WCF Test görünen İstemcisi'nde, ReverseString() yöntemi çift tıklayın. İstek bölmesinde girin `Sample` InputString parametresinin değeri. Tıklayın **çağırma**. Hizmet, "elpmaS" döndürmelidir.

### <a name="to-create-the-uppercaser-workflow-service"></a>UpperCaser iş akışı hizmeti oluşturma

1.  NestedServices projeye sağ tıklayıp **Ekle** > **yeni öğe**. İçinde **iş akışı** düğümünü **WCF iş akışı hizmeti**ve yeni hizmet adı `UpperCaserService`. **Ekle**'yi tıklatın. Bu projeye UpperCaserService.xamlx adlı yeni bir iş akışı hizmeti eklemeniz gerekir.

2.  UpperCaserService.xamlx Tasarımcısı'nda açın ve mevcut **ReceiveRequest** ve `SendReply` etkinlikleri ve sürükleme bir `ReceiveAndSendReply` mevcut sıralama etkinliğine etkinliğini.

    1.  Ayarlama **OperationName** UpperCaseString için.

    2.  Ayarlama **ServiceContractName** IUpperCaseString için.

    3.  Seçin **CanCreateInstance** onay kutusu.

3.  SequentialService etkinliği seçin ve ardından **değişkenleri** Tasarımcısı'nın altındaki sekmesi. Üç yeni değişkenleri StringToUpper StringToReverse ve dize türünde StringToReturn adlı oluşturun.

4.  Tıklayın **tanımla** bağlantısını **alma** etkinlik. Tıklayın **parametreleri**ve adlı InputString StringToUpper için atar String türünde bir parametre oluşturun.

5.  Tıklayın **tanımla** bağlantısını **SendReplyToReceive** etkinlik. Tıklayın **parametreleri**ve ModifiedString StringToReturn için atanan türü dize adlı bir parametre oluşturun.

6.  Hizmet mantığını uygulamak için aşağıdaki kodu kullanarak StringLibrary sınıfta yeni bir yöntem oluşturun.

    ```
    public static String UpperCaseString(string StringToUpperCase)
    {
         return StringToUpperCase.ToUpper();

    }
    ```

7.  Giriş UpperCaseString yöntemi çağırmak için sürükleyin bir **InvokeMethod** etkinliğini araç kutusundan arasındaki boşluk **alma** ve **SendReply** etkinlikler. Etkinlik özelliklerini şu şekilde ayarlayın:

    1.  **MethodName**: UpperCaseString

    2.  **Sonuç**: StringToReverse

    3.  **Parametreleri**: ile yeni parametre oluşturma bir **yönü** 'ın içinde bir **türü** dizesini ve **değer** StringToUpper.

    4.  **TargetType**: NestedServices.StringLibrary

8.  İlk hizmetidir şimdi değiştirilmiş dizesine ararız. Projeye sağ tıklayıp **Ekle** > **hizmet başvurusu**. Hizmetin bir hizmet Başvurusu Ekle http://localhost/NestedServices/StringReverserService.xamlx ve ilk Web hizmetine erişmek için özel bir etkinlik oluşturmak için projeyi derleyin.

9. Yeni Etkinlik örneği arasında iş akışı sürükleyin **InvokeMethod** etkinlik ve **SendReplyToReceive** etkinlikler. Değişken StringToReverse InputString özelliği yeni etkinliği ve değişken StringToReturn StringToReturn özelliğine atayın.

10. NestedServices projesi için Özellikler sayfasını açın ve değiştirmek **belirli sayfa** içinde **Web** UpperCaserService.xamlx için sekmesinde.

11. F5 tuşuna basarak test hizmeti. WCF Test görünen İstemcisi'nde, ReverseString() yöntemi çift tıklayın. İstek bölmesinde girin `Sample` InputString parametresinin değeri. Tıklayın **çağırma**. Hizmet, "ELPMAS" döndürmelidir.

### <a name="to-create-a-client-to-call-the-services"></a>Hizmetleri çağıran istemciye oluşturmak için

1.  İstemci çözümü olarak adlandırılan yeni bir konsol uygulama projesi ekleyin.

2.  İstemci projeye sağ tıklayıp **Ekle** > **hizmet başvurusu**. Açılan pencerede **bulma**. StringReverserService.xamlx seçin ve ad alanı ReverseService girin.  **Tamam**'ı tıklatın.

3.  Program.CS'de Webhostbuilder'a Main yöntemini aşağıdaki kodla değiştirin.

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