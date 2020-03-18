---
title: 'Walkthrough: C kullanarak bir Nesneyi Kalıcı #'
ms.date: 04/26/2018
ms.openlocfilehash: 85c5d1b711180eda5734d5860d996242c6bc89d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167576"
---
# <a name="walkthrough-persisting-an-object-using-c"></a>Walkthrough: C kullanarak bir nesneyi kalıcı\#

Bir nesnenin verilerini örnekler arasında kalıcı kılmak için serileştirmeyi kullanabilirsiniz, bu da değerleri depolamanızı ve nesnenin bir sonraki anında elde edildiği nde bunları almanızı sağlar.

Bu gözden geçirmede, temel `Loan` bir nesne oluşturur ve verilerini bir dosyada devam ettirmeye devam erecektir. Nesneyi yeniden oluşturduğunuzda dosyadaki verileri alırsınız.

> [!IMPORTANT]
> Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur. Bir uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için `Create` izni olmalıdır. İzinler erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten varsa, uygulamanın `Write` yalnızca izin, daha az izin gerekir. Mümkün olduğunda, dosyayı dağıtım sırasında oluşturmak ve yalnızca `Read` tek bir dosyaya izin vermek (klasör için izin oluşturma yerine) daha güvenlidir. Ayrıca, kullanıcı klasörlerine veri yazmak kök klasöre veya Program Dosyaları klasörüne yazmaktan daha güvenlidir.

> [!IMPORTANT]
> Bu örnek, verileri ikili biçim dosyasında depolar. Bu biçimler parolalar veya kredi kartı bilgileri gibi hassas veriler için kullanılmamalıdır.

## <a name="prerequisites"></a>Önkoşullar

- Oluşturmak ve çalıştırmak için [.NET Core SDK'yı](https://dotnet.microsoft.com/download)yükleyin.

- Daha önce yapmadıysanız, en sevdiğiniz kod düzenleyicisini yükleyin.

> [!TIP]
> Bir kod düzenleyicisi yüklemeniz mi gerekiyor? [Visual Studio'yı](https://visualstudio.com/downloads)deneyin!

- Örnek, C# 7.3 gerektirir. Bkz. [C# dil sürümünü seçin](../../../language-reference/configure-language-version.md)

Örnek kodu [.NET örnekleri GitHub deposundan](https://github.com/dotnet/samples/tree/master/csharp/serialization)online olarak inceleyebilirsiniz.

## <a name="creating-the-loan-object"></a>Kredi nesnesini oluşturma

İlk adım, sınıfı `Loan` kullanan bir sınıf ve konsol uygulaması oluşturmaktır:

1. Yeni bir uygulama oluşturun. Adlı `dotnet new console -o serialization` `serialization`bir alt dizinde yeni bir konsol uygulaması oluşturmak için yazın.
1. Düzenleyicinizde uygulamayı açın ve '' adlı `Loan.cs`yeni bir sınıf ekleyin.
1. Sınıfınıza `Loan` aşağıdaki kodu ekleyin:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

Ayrıca sınıfı kullanan bir uygulama oluşturmanız `Loan` gerekir.

## <a name="serialize-the-loan-object"></a>Ödünç nesneyi seri hale

1. `Program.cs` dosyasını açın. Aşağıdaki kodu ekleyin:

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

Olay için bir olay `PropertyChanged` işleyicisi ve `Loan` nesneyi değiştirmek ve değişiklikleri görüntülemek için birkaç satır ekleyin. Eklemeleri aşağıdaki kodda görebilirsiniz:

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

Bu noktada, kodu çalıştırabilir ve geçerli çıktıyı görebilirsiniz:

```console
New customer value: Henry Clay
7.5
7.1
```

Bu uygulamayı tekrar tekrar çalıştırmak her zaman aynı değerleri yazar. Programı her çalıştırdığınızda yeni bir Kredi nesnesi oluşturulur. Gerçek dünyada, faiz oranları periyodik olarak değişir, ancak uygulama çalıştırıldığı her zaman mutlaka değil. Serileştirme kodu, uygulama örnekleri arasındaki en son faiz oranını koruduğunuz anlamına gelir. Bir sonraki adımda, Kredi sınıfına serileştirme ekleyerek bunu yapacaksınız.

## <a name="using-serialization-to-persist-the-object"></a>Nesneyi Kalıcı Hale Getirmek için Serileştirme kullanma

Kredi sınıfının değerlerini devam ettirebilmek için, önce sınıfı `Serializable` öznitelikile işaretlemeniz gerekir. Kredi sınıfı tanımının üzerine aşağıdaki kodu ekleyin:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

Derleyiciye <xref:System.SerializableAttribute> sınıftaki her şeyin bir dosyada kalıcı olarak kalıcı olabileceğini söyler. `PropertyChanged` Olay nesne grafiğinin depolanacak bir bölümünü temsil etmediğinden seri hale getirilmemelidir. Bunu yapmak, bu olaya eklenen tüm nesneleri seri hale getirecektir. Olay işleyicisi için alan `PropertyChanged` bildirimine ekleyebilirsiniz. <xref:System.NonSerializedAttribute>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

C# 7.3 ile başlayarak, `field` hedef değeri kullanarak otomatik olarak uygulanan bir özelliğin destek alanına öznitelikleri ekleyebilirsiniz. Aşağıdaki kod bir `TimeLastLoaded` özellik ekler ve serileştirilebilir değil olarak işaretler:

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

Bir sonraki adım LoanApp uygulamasına serileştirme kodunu eklemektir. Sınıfı seri hale getirmek ve bir dosyaya yazmak <xref:System.IO> için, ve <xref:System.Runtime.Serialization.Formatters.Binary> ad boşluklarını kullanırsınız. Tam nitelikli adları yazmaktan kaçınmak için, aşağıdaki kodda gösterildiği gibi gerekli ad alanlarına referanslar ekleyebilirsiniz:

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

Bir sonraki adım, nesne oluşturulduğunda dosyadan nesneyi deserialize etmek için kod eklemektir. Serileştirilmiş verilerin dosya adı için sınıfa aşağıdaki kodda gösterildiği gibi sabit ekleyin:

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

Ardından, `TestLoan` nesneyi oluşturan satırdan sonra aşağıdaki kodu ekleyin:

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

Önce dosyanın var olup olmadığını denetlemeniz gerekir. Varsa, ikili dosyayı okumak için bir <xref:System.IO.Stream> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> sınıf ve dosyayı çevirmek için bir sınıf oluşturun. Ayrıca akış türünden Kredi nesnetürüne dönüştürmeniz gerekir.

Daha sonra bir dosyaya sınıf serileştirmek için kod eklemeniz gerekir. `Main` Yöntemde varolan koddan sonra aşağıdaki kodu ekleyin:

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

Bu noktada, uygulamayı yeniden oluşturabilir ve çalıştırabilirsiniz. İlk çalıştığında, faiz oranlarının 7,5'ten başlayıp 7,1'e değiştiğine dikkat edin. Uygulamayı kapatın ve yeniden çalıştırın. Şimdi, uygulama kaydedilen dosyayı okuduğu mesajını yazdırır ve faiz oranı, kodu değiştiren koddan önce bile 7,1'dir.

## <a name="see-also"></a>Ayrıca bkz.

- [Serileştirme (C# )](index.md)
- [C# Programlama Kılavuzu](../..//index.md)
