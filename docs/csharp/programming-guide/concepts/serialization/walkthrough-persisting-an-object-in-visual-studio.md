---
title: 'İzlenecek yol: kullanarak bir nesneyi kalıcı hale getirmeC#'
ms.date: 04/26/2018
ms.openlocfilehash: 9531909bdf1ed61305c292411ef2cd08b7b67465
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240473"
---
# <a name="walkthrough-persisting-an-object-using-c"></a>İzlenecek yol: C\# kullanarak bir nesneyi kalıcı hale getirme

Nesneleri, değerleri depolamanızı ve nesnenin bir sonraki açılışında bunları almanızı sağlayan örnekler arasında bir nesnenin verilerini kalıcı hale getirmek için serileştirme kullanabilirsiniz.

Bu kılavuzda, temel bir `Loan` nesnesi oluşturacak ve verilerini bir dosyaya kalıcı hale getirilecektir. Daha sonra nesneyi yeniden oluşturduğunuzda dosyadaki verileri buradan alırsınız.

> [!IMPORTANT]
> Bu örnek, dosya henüz yoksa yeni bir dosya oluşturur. Bir uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için `Create` izni olması gerekir. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten mevcutsa, uygulamanın daha az bir izin `Write` izni olması gerekir. Mümkün olduğunda, dağıtım sırasında dosyayı oluşturmak ve yalnızca tek bir dosyaya `Read` izinleri vermek (bir klasör için izinler oluşturmak yerine) için daha güvenlidir. Ayrıca, Kullanıcı klasörlerine veri yazmak, kök klasör veya Program Files klasöründen daha güvenlidir.

> [!IMPORTANT]
> Bu örnek, verileri bir ikili biçim dosyasında depolar. Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas veriler için kullanılmamalıdır.

## <a name="prerequisites"></a>Önkoşullar

- Derlemek ve çalıştırmak için [.NET Core SDK](https://dotnet.microsoft.com/download)' yi çalıştırın.

- Henüz yapmadıysanız, en sevdiğiniz kod düzenleyicinizi yükleyebilirsiniz.

> [!TIP]
> Bir kod Düzenleyicisi yüklemeniz mı gerekiyor? [Visual Studio 'yu](https://visualstudio.com/downloads)deneyin!

- Örnek 7,3 gerektirir C# . Bkz [. C# dil sürümünü seçme](../../../language-reference/configure-language-version.md) 

Örnek kodu, [.NET örnekleri GitHub deposunda](https://github.com/dotnet/samples/tree/master/csharp/serialization)çevrimiçi olarak inceleyebilirsiniz.

## <a name="creating-the-loan-object"></a>Kredi nesnesi oluşturma

İlk adım, sınıfı kullanan bir `Loan` sınıfı ve konsol uygulaması oluşturmaktır:

1. Yeni bir uygulama oluşturun. `serialization`adlı bir alt dizinde yeni bir konsol uygulaması oluşturmak için `dotnet new console -o serialization` yazın.
1. Düzenleyicinizde uygulamayı açın ve `Loan.cs`adlı yeni bir sınıf ekleyin.
1. `Loan` Sınıfınıza aşağıdaki kodu ekleyin:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

Ayrıca, `Loan` sınıfını kullanan bir uygulama da oluşturmanız gerekir.

## <a name="serialize-the-loan-object"></a>Kredi nesnesini seri hale getirme

1. `Program.cs` programını açın. Aşağıdaki kodu ekleyin:

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

`PropertyChanged` olayı için bir olay işleyicisi ve `Loan` nesnesini değiştirmek ve değişiklikleri göstermek için birkaç satır ekleyin. Eklemeleri aşağıdaki kodda görebilirsiniz:

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

Bu noktada, kodu çalıştırabilir ve geçerli çıktıyı görebilirsiniz:

```console
New customer value: Henry Clay
7.5
7.1
```

Bu uygulamayı sürekli olarak çalıştırmak her zaman aynı değerleri yazar. Programı her çalıştırdığınızda yeni bir kredi nesnesi oluşturulur. Gerçek dünyada, faiz oranları düzenli aralıklarla değişir, ancak uygulama her çalıştırıldığında her zaman gerekli değildir. Serileştirme kodu, uygulamanın örnekleri arasındaki en son faiz oranını koruduğunuzdan anlamına gelir. Bir sonraki adımda, yalnızca kredi sınıfına serileştirme ekleyerek bunu yapacaksınız.

## <a name="using-serialization-to-persist-the-object"></a>Nesneyi kalıcı hale getirmek için serileştirme kullanma

Kredi sınıfının değerlerini kalıcı hale getirmek için önce sınıfı `Serializable` özniteliğiyle işaretlemeniz gerekir. Aşağıdaki kodu ödünç verme sınıfı tanımının üzerine ekleyin:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

<xref:System.SerializableAttribute> derleyiciye sınıftaki her şeyin bir dosyaya kalıcı hale, olduğunu söyler. `PropertyChanged` olay depolanması gereken nesne grafiğinin bir parçasını temsil etmediğinden, serileştirilmemelidir. Bunun yapılması, bu olaya eklenmiş tüm nesneleri serileştirilir. <xref:System.NonSerializedAttribute> `PropertyChanged` olay işleyicisi için alan bildirimine ekleyebilirsiniz.

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

7,3 ' C# den başlayarak, `field` Target değerini kullanarak otomatik uygulanan bir özelliğin yedekleme alanına öznitelikler ekleyebilirsiniz. Aşağıdaki kod `TimeLastLoaded` bir özelliği ekler ve onu seri hale getirilebilir değil olarak işaretler:

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

Sonraki adım, ödünç uygulama uygulamasına serileştirme kodu eklemektir. Sınıfını seri hale getirmek ve bir dosyaya yazmak için <xref:System.IO> ve <xref:System.Runtime.Serialization.Formatters.Binary> ad alanlarını kullanırsınız. Tam nitelikli adları yazmayı önlemek için, aşağıdaki kodda gösterildiği gibi gerekli ad alanlarına başvurular ekleyebilirsiniz:

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

Sonraki adım, nesne oluşturulduğunda nesnenin serisini kaldırmak için kod eklemektir. Aşağıdaki kodda gösterildiği gibi serileştirilmiş verilerin dosya adı sınıfına bir sabit ekleyin:

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

Sonra, `TestLoan` nesnesini oluşturan satırdan sonra aşağıdaki kodu ekleyin:

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

Önce dosyanın var olduğunu denetlemeniz gerekir. Varsa, dosyayı çevirmek için ikili dosyayı ve bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> sınıfını okumak üzere bir <xref:System.IO.Stream> sınıfı oluşturun. Akış türünden kredi nesne türüne de dönüştürmeniz gerekir.

Daha sonra, sınıfı bir dosyaya seri hale getirmek için kod eklemeniz gerekir. `Main` yönteminde Varolan koddan sonra aşağıdaki kodu ekleyin:

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

Bu noktada, uygulamayı derleyip çalıştırabilirsiniz. İlk kez çalıştırıldığında, faiz oranlarının 7,5 ' de başlayacağını ve sonra 7,1 olarak değiştiğine dikkat edin. Uygulamayı kapatın ve sonra yeniden çalıştırın. Artık uygulama, kaydedilen dosyayı okudığı iletiyi yazdırır ve faiz oranı, kodu değiştiren koddan önce bile 7,1 olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Serileştirme (C#)](index.md)
- [C# Programlama Kılavuzu](../..//index.md)
