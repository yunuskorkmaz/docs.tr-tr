---
title: 'İzlenecek yol: C# kullanarak bir nesneyi kalıcı kılma'
ms.date: 04/26/2018
ms.openlocfilehash: 6c9719dc3aaf997ea144515a553f787450e54041
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="walkthrough-persisting-an-object-using-c"></a>İzlenecek yol: C# kullanarak bir nesneyi kalıcı kılma #

Bir nesnenin veri değerlerini depolamak ve nesne örneği bir sonraki başlatılışında almak sağlar örnekleri arasında kalıcı hale getirmek için seri hale getirme kullanabilirsiniz.

Bu kılavuzda, temel oluşturacak `Loan` nesne ve verileri bir dosyaya kalır. Nesne yeniden oluşturduğunuzda, ardından dosyadan verileri alır.

> [!IMPORTANT]
> Bu örnek, dosyanın zaten mevcut değilse yeni bir dosya oluşturur. Bir uygulama bir dosya oluşturmanız gerekiyorsa, bu uygulamanın olmalıdır `Create` klasörü için izni. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` izin, daha az izni. Mümkünse, dağıtım sırasında dosyası oluşturma ve yalnızca izni daha güvenli olan `Read` (yerine bir klasör izinlerini Oluştur) tek bir dosya izni. Ayrıca, kök klasöre veya Program dosyaları klasörü kullanıcı klasörleri verileri yazmak amacıyla daha güvenlidir.

> [!IMPORTANT]
> Bu örnek verileri bir ikili biçimi dosyasında depolar. Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas verileri için kullanılmamalıdır.

## <a name="prerequisites"></a>Önkoşullar

* Derleme ve çalıştırma için yükleme [.NET Core SDK](https://www.microsoft.com/net/core).

* Henüz yapmadıysanız, sık kullanılan kod düzenleyicisinde yükleyin.

> [!TIP]
> Kod Düzenleyicisi yüklemeniz gerekiyor? Deneyin [Visual Studio](https://visualstudio.com/downloads)!

Örnek kodu çevrimiçi inceleyebilirsiniz [.NET örnekleri GitHub deposunda](https://github.com/dotnet/samples/tree/master/csharp/serialization).

## <a name="creating-the-loan-object"></a>Kredi nesnesi oluşturma

İlk adım oluşturmaktır bir `Loan` sınıfı ve sınıfını kullanan bir konsol uygulaması:

1. Yeni bir uygulama oluşturun. Tür `dotnet new console -o serialization` adlı bir alt dizinde yeni bir konsol uygulaması oluşturmak için `serialization`.
1. Uygulama, düzenleyicisinde açın ve adlı yeni bir sınıf ekleyin `Loan.cs`.
1. Aşağıdaki kodu ekleyin, `Loan` sınıfı:

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

Ayrıca kullanan bir uygulama oluşturmanız gerekir `Loan` sınıfı.

## <a name="serialize-the-loan-object"></a>Kredi nesneyi serileştirme

1. Açık `Program.cs`. Aşağıdaki kodu ekleyin:

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

Bir olay işleyicisi ekleme `PropertyChanged` olay ve değiştirmek için birkaç satır `Loan` nesne ve değişiklikleri görüntüleyin. Aşağıdaki kodda eklemeleri görebilirsiniz:

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

Bu noktada, kodu çalıştırın ve geçerli çıkış bakın:

```console
New customer value: Henry Clay
7.5
7.1
```

Sürekli olarak her zaman bu uygulamayı çalıştıran aynı değerlere yazar. Program çalıştır her zaman yeni bir kredi nesnesi oluşturulur. Gerçek Hayatta, faiz oranları uygulama her çalıştırıldığında düzenli aralıklarla, ancak mutlaka değiştirin. Seri hale getirme kodu uygulama örnekleri arasında en son faiz oranını korumak anlamına gelir. Sonraki adımda, yalnızca serileştirme kredisi sınıfına ekleyerek bunu.

## <a name="using-serialization-to-persist-the-object"></a>Nesne kalıcı hale getirmek için seri hale getirme kullanma

Kredi sınıfı için değerleri kalıcı hale getirmek için önce sınıfıyla işaretlemelisiniz `Serializable` özniteliği. Kredi sınıf tanımı üzerinde aşağıdaki kodu ekleyin:

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<xref:System.SerializableAttribute> Derleyici sınıftaki her şeyi bir dosyaya kalıcı olduğunu bildirir. Çünkü `PropertyChanged` olay depolanması gereken nesne grafiğin parçası temsil etmez, sıralanmamış. Bunun yapılması, bu olaya bağlı olan tüm nesneleri seri hale. Ekleyebileceğiniz <xref:System.NonSerializedAttribute> için alan bildirimini için `PropertyChanged` olay işleyicisi.

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

C# 7.3 ile başlayarak, bir otomatik uygulanan özelliğini kullanarak, yedekleme alanını öznitelikler ekleyebilirsiniz `field` hedef değeri. Aşağıdaki kod ekler bir `TimeLastLoaded` özelliği ve getirilemez olarak işaretler:

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

Sonraki adım, LoanApp uygulamaya serileştirme kod eklemektir. Sınıf seri hale getirmek ve bir dosyaya yazmak için kullandığınız <xref:System.IO> ve <xref:System.Runtime.Serialization.Formatters.Binary> ad alanları. Tam olarak nitelenmiş adlar yazma zorunluluğunu ortadan kaldırmak için aşağıdaki kodda gösterildiği gibi gerekli ad alanlarına başvurular ekleyebilirsiniz:

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

Sonraki adım, nesne oluşturulduğunda dosyasından nesnesi seri durumdan çıkarılacak kod eklemektir. Aşağıdaki kodda gösterildiği gibi serileştirilmiş verilerinin dosya adı için sınıf için bir sabit ekleyin:

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

Ardından, oluşturan satırından sonra aşağıdaki kodu ekleyin `TestLoan` nesnesi:

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

İlk dosyanın var olduğunu işaretlemeniz gerekir. Varsa oluşturma bir <xref:System.IO.Stream> ikili dosya okuma için sınıf ve <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> dosyayı çevirmek için sınıf. Ayrıca akış türünden kredisi nesne türüne dönüştürmeniz gerekir.

Sonraki sınıfı bir dosyaya serileştirmek için kod eklemeniz gerekir. Var olan koddan sonra aşağıdaki kodu ekleyin `Main` yöntemi:

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

Bu noktada, yeniden yapılandırabilir ve uygulamayı çalıştırın. Bunu, ilk çalıştığında faiz oranları 7.5 başlatır ve 7.1 için değişiklikler dikkat edin. Uygulamayı kapatın ve yeniden çalıştırın. Şimdi, uygulama ileti kaydedilen dosya okudu ve hatta değiştiğinde kodundan önce 7.1 faiz oranıdır yazdırır.

## <a name="see-also"></a>Ayrıca bkz.

 [Serileştirme (C# )](index.md)  
 [C# Programlama Kılavuzu](../..//index.md)  
