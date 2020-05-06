---
title: 'İzlenecek yol: C kullanarak bir nesneyi kalıcı hale getirme #'
ms.date: 04/26/2018
ms.openlocfilehash: bbe239008629d687084af7e28a75fa68560ca0ab
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796073"
---
# <a name="walkthrough-persisting-an-object-using-c"></a>İzlenecek yol: C kullanarak bir nesneyi kalıcı hale getirme\#

Nesneleri, değerleri depolamanızı ve nesnenin bir sonraki açılışında bunları almanızı sağlayan örnekler arasında bir nesnenin verilerini kalıcı hale getirmek için serileştirme kullanabilirsiniz.

Bu kılavuzda, temel `Loan` bir nesne oluşturacak ve verilerini bir dosyaya kalıcı hale getirilecektir. Daha sonra nesneyi yeniden oluşturduğunuzda dosyadaki verileri buradan alırsınız.

> [!IMPORTANT]
> Bu örnek, dosya henüz yoksa yeni bir dosya oluşturur. Bir uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için izni `Create` olması gerekir. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten varsa, uygulamanın daha az izne sahip yalnızca `Write` izne ihtiyacı vardır. Mümkün olduğunda, dağıtım sırasında dosyayı oluşturmak ve yalnızca tek bir dosyaya (bir klasör için `Read` izinler oluşturmak yerine) izin vermek daha güvenlidir. Ayrıca, Kullanıcı klasörlerine veri yazmak, kök klasör veya Program Files klasöründen daha güvenlidir.

> [!IMPORTANT]
> Bu örnek, verileri bir ikili biçim dosyasında depolar. Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas veriler için kullanılmamalıdır.

## <a name="prerequisites"></a>Ön koşullar

- Derlemek ve çalıştırmak için [.NET Core SDK](https://dotnet.microsoft.com/download)' yi çalıştırın.

- Henüz yapmadıysanız, en sevdiğiniz kod düzenleyicinizi yükleyebilirsiniz.

> [!TIP]
> Bir kod Düzenleyicisi yüklemeniz mı gerekiyor? [Visual Studio 'yu](https://visualstudio.com/downloads)deneyin!

- Örnek, C# 7,3 gerektirir. Bkz [. C# dil sürümünü seçme](../../../language-reference/configure-language-version.md)

Örnek kodu, [.NET örnekleri GitHub deposunda](https://github.com/dotnet/samples/tree/master/csharp/serialization)çevrimiçi olarak inceleyebilirsiniz.

## <a name="creating-the-loan-object"></a>Kredi nesnesi oluşturma

İlk adım, sınıfını kullanan bir `Loan` sınıf ve konsol uygulaması oluşturmaktır:

1. Yeni bir uygulama oluşturun. Adlı `dotnet new console -o serialization` `serialization`bir alt dizinde yeni bir konsol uygulaması oluşturmak için yazın.
1. Düzenleyicinizde uygulamayı açın ve adlı `Loan.cs`yeni bir sınıf ekleyin.
1. Sınıfınıza `Loan` aşağıdaki kodu ekleyin:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

Ayrıca, `Loan` sınıfını kullanan bir uygulama da oluşturmanız gerekecektir.

## <a name="serialize-the-loan-object"></a>Kredi nesnesini seri hale getirme

1. `Program.cs` dosyasını açın. Aşağıdaki kodu ekleyin:

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

`PropertyChanged` Olay için bir olay işleyicisi ve `Loan` nesneyi değiştirmek ve değişiklikleri göstermek için birkaç satır ekleyin. Eklemeleri aşağıdaki kodda görebilirsiniz:

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

Bu noktada, kodu çalıştırabilir ve geçerli çıktıyı görebilirsiniz:

```console
New customer value: Henry Clay
7.5
7.1
```

Bu uygulamayı sürekli olarak çalıştırmak her zaman aynı değerleri yazar. Programı her çalıştırdığınızda yeni bir kredi nesnesi oluşturulur. Gerçek dünyada, faiz oranları düzenli aralıklarla değişir, ancak uygulama her çalıştırıldığında her zaman gerekli değildir. Serileştirme kodu, uygulamanın örnekleri arasındaki en son faiz oranını koruduğunuzdan anlamına gelir. Bir sonraki adımda, yalnızca kredi sınıfına serileştirme ekleyerek bunu yapacaksınız.

## <a name="using-serialization-to-persist-the-object"></a>Nesneyi kalıcı hale getirmek için serileştirme kullanma

Kredi sınıfının değerlerini kalıcı hale getirmek için, önce sınıfı `Serializable` özniteliğiyle işaretlemeniz gerekir. Aşağıdaki kodu ödünç verme sınıfı tanımının üzerine ekleyin:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

, <xref:System.SerializableAttribute> Derleyiciye sınıftaki her şeyin bir dosyaya kalıcı olarak devam edebilir olduğunu söyler. `PropertyChanged` Olay, nesne grafiğinin depolanması gereken parçasını temsil etmediğinden, serileştirilmemelidir. Bunun yapılması, bu olaya eklenmiş tüm nesneleri serileştirilir. Olay işleyicisi için alan bildirimine ekleyebilirsiniz <xref:System.NonSerializedAttribute> `PropertyChanged`

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

C# 7,3 ' den başlayarak, `field` hedef değeri kullanarak otomatik uygulanan bir özelliğin yedekleme alanına öznitelikler ekleyebilirsiniz. Aşağıdaki kod bir `TimeLastLoaded` özellik ekler ve onu seri hale getirilebilir değil olarak işaretler:

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

Sonraki adım, ödünç uygulama uygulamasına serileştirme kodu eklemektir. Sınıfını seri hale getirmek ve bir dosyaya yazmak için, <xref:System.IO> ve <xref:System.Runtime.Serialization.Formatters.Binary> ad alanlarını kullanırsınız. Tam nitelikli adları yazmayı önlemek için, aşağıdaki kodda gösterildiği gibi gerekli ad alanlarına başvurular ekleyebilirsiniz:

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

Sonraki adım, nesne oluşturulduğunda nesnenin serisini kaldırmak için kod eklemektir. Aşağıdaki kodda gösterildiği gibi serileştirilmiş verilerin dosya adı sınıfına bir sabit ekleyin:

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

Sonra, `TestLoan` nesneyi oluşturan satırdan sonra aşağıdaki kodu ekleyin:

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

Önce dosyanın var olduğunu denetlemeniz gerekir. Varsa, ikili dosyayı okumak için <xref:System.IO.Stream> bir sınıf ve dosyayı çevirecek bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> sınıf oluşturun. Akış türünden kredi nesne türüne de dönüştürmeniz gerekir.

Daha sonra, sınıfı bir dosyaya seri hale getirmek için kod eklemeniz gerekir. `Main` Yöntemdeki mevcut koddan sonra aşağıdaki kodu ekleyin:

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

Bu noktada, uygulamayı derleyip çalıştırabilirsiniz. İlk kez çalıştırıldığında, faiz oranlarının 7,5 ' de başlayacağını ve sonra 7,1 olarak değiştiğine dikkat edin. Uygulamayı kapatın ve sonra yeniden çalıştırın. Artık uygulama, kaydedilen dosyayı okudığı iletiyi yazdırır ve faiz oranı, kodu değiştiren koddan önce bile 7,1 olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Serileştirme (C# )](index.md)
- [C# Programlama Kılavuzu](../../index.md)
