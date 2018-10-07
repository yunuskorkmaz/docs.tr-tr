---
title: 'İzlenecek yol: C# kullanarak bir nesneyi kalıcı kılma'
ms.date: 04/26/2018
ms.openlocfilehash: 85c447ae43086cc789338e77555b7400a523662a
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847925"
---
# <a name="walkthrough-persisting-an-object-using-c"></a>İzlenecek yol: C# kullanarak bir nesneyi kalıcı kılma #

Seri hale getirme, bir nesnenin veri değerleri depolamak ve bunları nesnesi örneği başlatıldığında almanıza imkan tanıyan örnekler arasında kalıcı hale getirmek için kullanabilirsiniz.

Bu kılavuzda, bir temel oluşturacak `Loan` nesne ve verileri bir dosyaya kalıcı. Nesne yeniden oluşturduğunuzda dosyadan verileri ardından alır.

> [!IMPORTANT]
> Bu örnek, bir dosya zaten mevcut değilse yeni bir dosya oluşturur. Bir uygulama bir dosya oluşturmanız gerekiyorsa, bu uygulamanın olmalıdır `Create` klasörüne izni. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` izin, daha düşük bir izni. Mümkün olan yerlerde, dosyayı dağıtım sırasında oluşturmak ve yalnızca daha güvenli olan `Read` izinleri tek bir dosya (yerine bir klasörün izinlerini oluşturma). Ayrıca, kök klasöre veya Program dosyaları klasörüne kullanıcı klasörleri verileri yazmak amacıyla daha güvenlidir.

> [!IMPORTANT]
> Bu örnek, verileri bir ikili biçimi dosyasında depolar. Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas veriler için kullanılmamalıdır.

## <a name="prerequisites"></a>Önkoşullar

* Derlemek ve çalıştırmak için yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/core).

* Henüz yapmadıysanız, sık kullandığınız kod düzenleyicinize yükleyin.

> [!TIP]
> Bir kod Düzenleyicisi'ni yüklemeniz gerekir? Deneyin [Visual Studio](https://visualstudio.com/downloads)!

* Örnek C# 7.3 gerektirir. Bkz: [C# dil sürümünü seçin](../../../language-reference/configure-language-version.md) 

Örnek kodu inceleyebilirsiniz [.NET örnekleri GitHub deposunda](https://github.com/dotnet/samples/tree/master/csharp/serialization).

## <a name="creating-the-loan-object"></a>Kredi nesnesi oluşturma

İlk adım oluşturmaktır bir `Loan` sınıfı ve sınıfını kullanan bir konsol uygulaması:

1. Yeni bir uygulama oluşturun. Tür `dotnet new console -o serialization` adlı bir alt dizinde yeni bir konsol uygulaması oluşturmak için `serialization`.
1. Uygulama düzenleyicinizde açın ve adlı yeni bir sınıf ekleyin `Loan.cs`.
1. Aşağıdaki kodu ekleyin, `Loan` sınıfı:

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

Ayrıca kullanan bir uygulama oluşturmanız gerekir `Loan` sınıfı.

## <a name="serialize-the-loan-object"></a>Kredi nesne seri hale getirme

1. Açık `Program.cs`. Aşağıdaki kodu ekleyin:

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

İçin bir olay işleyicisi ekleme `PropertyChanged` olay ve değiştirmek için birkaç satır kod `Loan` nesne ve değişiklikleri görüntüleyin. Aşağıdaki kodda eklemeleri görebilirsiniz:

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

Bu noktada, kodu çalıştırmak ve geçerli bir çıktı görürsünüz:

```console
New customer value: Henry Clay
7.5
7.1
```

Art arda her zaman bu uygulamayı çalıştıran değerlerine yazar. Programı her çalıştırdığınızda, yeni bir kredi nesnesi oluşturulur. Gerçek dünyada, uygulama her çalıştırıldığında düzenli aralıklarla ancak bu şart değildir faiz oranları değiştirin. Serileştirme kodu, uygulama örnekleri arasında en son faiz oranını korumak anlamına gelir. Sonraki adımda, yalnızca kredi sınıfı seri hale getirme ekleyerek bunu.

## <a name="using-serialization-to-persist-the-object"></a>Nesne kalıcı hale getirmek için serileştirme kullanma

Kredi sınıfı değerlerini kalıcı hale getirmek için önce sınıfıyla işaretlemelisiniz `Serializable` özniteliği. Yukarıda kredi sınıf tanımına aşağıdaki kodu ekleyin:

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<xref:System.SerializableAttribute> Sınıftaki her şeyi bir dosyaya kalıcı olduğunu bildirir. Çünkü `PropertyChanged` olay temsil depolanmalıdır nesne grafiğinin parçası, sıralanmamış. Bunun yapılması, bu olaya bağlı tüm nesnelerini seri hale getirmek. Ekleyebileceğiniz <xref:System.NonSerializedAttribute> için alan bildirimini için `PropertyChanged` olay işleyicisi.

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

C# 7.3 ile başlayarak, öznitelikleri kullanarak bir otomatik uygulanan özellik, yedekleme alanını ekleyebilirsiniz `field` hedef değer. Aşağıdaki kodu ekler bir `TimeLastLoaded` özelliği ve nelze serializovat olarak işaretler:

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

Sonraki adım, LoanApp uygulamaya serileştirme kodu eklemektir. Sınıf seri hale getirmek ve bir dosyaya yazmak için kullanmanız <xref:System.IO> ve <xref:System.Runtime.Serialization.Formatters.Binary> ad alanları. Tam nitelikli adlarını yazarak önlemek için aşağıdaki kodda gösterildiği gibi gerekli ad alanlarına başvurular ekleyebilirsiniz:

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

Sonraki adım, bir nesne oluşturulduğunda dosyasından nesnesi seri durumdan çıkarılacak kod eklemektir. Sınıfına aşağıdaki kodda gösterildiği gibi seri hale getirilmiş veri dosya adı için bir sabit ekleyin:

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

Ardından, aşağıdaki kodu oluşturan bir satırın sonunda ekleyin `TestLoan` nesnesi:

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

İlk dosyasının varolduğunu işaretlemeniz gerekir. Yoksa, oluşturun bir <xref:System.IO.Stream> ikili dosyayı okumak için sınıf ve <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> dosya çevirmek için sınıf. Ayrıca akış türünden kredi nesne türüne dönüştürmek gerekir.

Sonraki sınıfı bir dosyaya serileştirmek için kod eklemeniz gerekir. Varolan kod içine aşağıdaki kodu ekleyin `Main` yöntemi:

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

Bu noktada, yeniden derleyebilir ve uygulamayı çalıştırın. İlk kez çalıştığında, faiz oranları 7.5 başlar ve ardından 7.1 için değişiklikleri dikkat edin. Uygulamayı kapatın ve yeniden çalıştırın. Şimdi uygulamayı kaydedilen dosyayı okudu ve 7.1 bile, değişiklikleri kodundan önce faiz oranını olduğundan ileti yazdırır.

## <a name="see-also"></a>Ayrıca Bkz.

- [Seri hale getirme (C#)](index.md)  
- [C# Programlama Kılavuzu](../..//index.md)  
