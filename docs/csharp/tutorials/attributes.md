---
title: 'Öğretici: Öznitelikleri kullanın - C #'
description: Özniteliklerin C#'da nasıl çalıştığını öğrenin.
author: mgroves
ms.technology: csharp-fundamentals
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: 24cb7d35a89fda78511dc4ba725b69c5d601a008
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937465"
---
# <a name="use-attributes-in-c"></a>C'de Öznitelikleri Kullanma\#

Öznitelikler, bilgileri kodla bildirimsel bir şekilde ilişkilendirme nin bir yolunu sağlar. Ayrıca, çeşitli hedeflere uygulanabilecek yeniden kullanılabilir bir öğe de sağlayabilirler.

`[Obsolete]` Özniteliği göz önünde bulundurun. Sınıflara, yapılara, yöntemlere, yapıcılara ve daha fazlasına uygulanabilir. Öğenin eski olduğunu _bildirir._ Daha sonra bu özniteliği aramak ve yanıt olarak bazı eylem yapmak C# derleyicisine kalmış.

Bu öğreticide, kodunuza öznitelikleri nasıl ekleyeceğiniz, kendi özniteliklerinizi nasıl oluşturacağınız ve kullanacağınız ve .NET Core'da yerleşik bazı özniteliklerin nasıl kullanılacağı ile tanışılırsınız.

## <a name="prerequisites"></a>Önkoşullar
.NET çekirdeğini çalıştırmak için makinenizi ayarlamanız gerekir. Yükleme yönergelerini [.NET Çekirdek İndirmeler](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz.
Bu uygulamayı Windows, Ubuntu Linux, macOS veya Docker kapsayıcısında çalıştırabilirsiniz.
En sevdiğiniz kod düzenleyicisini yüklemeniz gerekir. Aşağıdaki açıklamalar açık kaynak, çapraz platform düzenleyicisi [olan Visual Studio Code'u](https://code.visualstudio.com/) kullanabilmiştir. Ancak, hangi araçları ile rahat kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulamayı Oluştur

Artık tüm araçları yüklediğinize göre, yeni bir .NET Core uygulaması oluşturun. Komut satırı jeneratörü kullanmak için, en sevdiğiniz kabuk aşağıdaki komutu çalıştırın:

`dotnet new console`

Bu komut çıplak kemikler .NET çekirdek proje dosyaları oluşturur. Bu projeyi `dotnet restore` derlemek için gereken bağımlılıkları geri yüklemek için yürütmeniz gerekir.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Programı yürütmek için. `dotnet run` Konsolda "Merhaba, Dünya" çıktısını görmelisiniz.

## <a name="how-to-add-attributes-to-code"></a>Koda öznitelikler ekleme

C#'da `Attribute` öznitelikler, taban sınıftan devralan sınıflardır. Devralan `Attribute` herhangi bir sınıf, diğer kod parçalarında bir tür "etiket" olarak kullanılabilir.
Örneğin, adı verilen `ObsoleteAttribute`bir öznitelik vardır. Bu, kodun eski olduğunu ve artık kullanılmaması gerektiğini bildirmek için kullanılır. Bu özniteliği, örneğin kare ayraçlar kullanarak bir sınıfa yerleştirebilirsiniz.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]

Sınıf çağrılırken, `ObsoleteAttribute`yalnızca kodda kullanılması `[Obsolete]` gerektiğini unutmayın. Bu C#'nın takip ettiği bir kuraldır.
İsterseniz tam adı `[ObsoleteAttribute]` kullanabilirsiniz.

Bir sınıfı eski işaretleme yaparken, *neden* geçersiz olduğu ve/veya bunun yerine *ne* kullanılacağı hakkında bazı bilgiler vermek iyi bir fikirdir. Bunu, Eskisolete özniteliğine bir dize parametresi geçirerek yapın.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

Dize, sanki siz yazıyormuşsunuz `ObsoleteAttribute` `var attr = new ObsoleteAttribute("some string")`gibi, bir kurucuya bir argüman olarak geçiriliyor.

Bir öznitelik oluşturucuya parametreler basit türleri/ literals ile sınırlıdır: `bool, int, double, string, Type, enums, etc` ve bu tür dizileri.
Bir ifade veya değişken kullanamazsınız. Konumsal veya adlandırılmış parametreleri kullanmakta özgürsunuz.

## <a name="how-to-create-your-own-attribute"></a>Kendi özniteliğinizi oluşturma

Öznitelik `Attribute` oluşturmak, taban sınıftan devralmak kadar basittir.

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Yukarıdaki ile, şimdi kod `[MySpecial]` tabanında `[MySpecialAttribute]`başka bir özellik olarak (veya) kullanabilirsiniz.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

.NET taban sınıf kitaplığındaki öznitelikler derleyici `ObsoleteAttribute` içindeki belirli davranışları tetikler. Ancak, oluşturduğunuz herhangi bir öznitelik yalnızca meta veri olarak hareket eder ve öznitelik sınıfı içinde herhangi bir kod yürütülmektedir neden olmaz. Bu meta verilere kodunuzda başka bir yerde (daha sonra öğreticide bu konuda daha fazla) göre hareket etmek size kalmış.

Burada dikkat etmek için bir 'gotcha' var. Yukarıda belirtildiği gibi, öznitelikleri kullanırken yalnızca belirli türleri bağımsız değişken olarak geçirilebilir. Ancak, bir öznitelik türü oluştururken, C# derleyicisi bu parametreleri oluşturmanızı engellemez. Aşağıdaki örnekte, ben sadece iyi derleyen bir oluşturucu ile bir öznitelik oluşturduk.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Ancak, öznitelik sözdizimi ile bu oluşturucu kullanmak mümkün olmayacaktır.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

Yukarıdaki gibi bir derleyici hatasına neden olur`Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>Öznitelik kullanımı nasıl kısıtlar?

Öznitelikler bir dizi "hedef" üzerinde kullanılabilir. Yukarıdaki örnekler sınıflarda bunları gösterir, ancak bunlar da kullanılabilir:

* Derleme
* Sınıf
* Oluşturucu
* Temsilci
* Sabit Listesi
* Olay
* Alan
* Genel Parametre
* Arabirim
* Yöntem
* Modül
* Parametre
* Özellik
* Returnvalue
* Yapı

Varsayılan olarak bir öznitelik sınıfı oluşturduğunuzda, C# bu özniteliği olası öznitelik hedeflerinden herhangi birinde kullanmanıza izin verir. Öznitelikinizi belirli hedeflerle sınırlamak istiyorsanız, bunu öznitelik `AttributeUsageAttribute` sınıfınızdakileri kullanarak yapabilirsiniz. Bu doğru, bir öznitelik bir öznitelik!

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Yukarıdaki özniteliği sınıf veya yapı olmayan bir şeye koymaya çalışırsanız, derleyici hatası alırsınız`Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Kod öğesine iliştirilen öznitelikler nasıl kullanılır?

Öznitelikler meta veri olarak hareket eder. Dışa dönük bir güç olmadan hiçbir şey yapmazlar.

Öznitelikleri bulmak ve harekete geçebilmek için, [Yansıma'ya](../programming-guide/concepts/reflection.md) genellikle ihtiyaç vardır. Ben bu öğretici yansıma derinlemesine kapsamaz, ama temel fikir Yansıma diğer kodu inceler C # kod yazmak için izin verir.

Örneğin, bir sınıf hakkında bilgi almak için `using System.Reflection;` Reflection'u kullanabilirsiniz (kodunuzun başına ekle):

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

Bu gibi bir şey yazdıracak:`The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Bir `TypeInfo` nesneye (veya `MemberInfo`, `FieldInfo`vb.) sahip `GetCustomAttributes` olduktan sonra, yöntemi kullanabilirsiniz. Bu, nesnelerin bir `Attribute` koleksiyon döndürecek.
Ayrıca bir `GetCustomAttribute` Öznitelik türünü kullanabilir ve belirtebilirsiniz.

`GetCustomAttributes` Burada (daha `MemberInfo` önce gördüğümüz bir `MyClass` örnek üzerinde bir öznitelik vardır) kullanma nın bir `[Obsolete]` örneği var.

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

Bu konsola yazdıracak: `Attribute on MyClass: ObsoleteAttribute`. Diğer öznitelikleri `MyClass`eklemeyi deneyin.

Bu `Attribute` nesnelerin tembel bir şekilde anlık olarak fark edildiğini belirtmek önemlidir. Diğer bir zamanda, sen kullanana `GetCustomAttribute` kadar anlık `GetCustomAttributes`olarak lanse edilmeyecekler ya da.
Onlar da her zaman anlık vardır. Art `GetCustomAttributes` arda iki kez arama, iki `ObsoleteAttribute`farklı örneği döndürecektir.

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Taban sınıf kitaplığında ortak öznitelikler (BCL)

Öznitelikler birçok araç ve çerçeve tarafından kullanılır. NUnit, NUnit test koşucusu tarafından kullanılan gibi `[Test]` ve `[TestFixture]` öznitelikleri kullanır. ASP.NET MVC gibi `[Authorize]` öznitelikleri kullanır ve MVC eylemleri üzerinde çapraz kesme endişeleri gerçekleştirmek için bir eylem filtresi çerçevesi sağlar. [PostSharp,](https://www.postsharp.net) C#'da boy odaklı programlamaya izin vermek için öznitelik sözdizimini kullanır.

.NET Core taban sınıf kitaplıklarına dahil edilmiş birkaç önemli özellik şunlardır:

* `[Obsolete]`. Bu yukarıdaki örneklerde kullanılmıştır ve `System` ad alanında yaşıyor. Değişen kod tabanı hakkında bildirimsel belgeler sağlamak yararlıdır. İleti dize biçiminde sağlanabilir ve derleyici uyarısını derleyici hatasına çıkarmak için başka bir boolean parametresi kullanılabilir.

* `[Conditional]`. Bu öznitelik `System.Diagnostics` ad alanındadır. Bu öznitelik yöntemlere (veya öznitelik sınıflarına) uygulanabilir. Bir dizeyi oluşturucuya geçirmelisiniz.
Bu dize bir `#define` yönergeyle eşleşmiyorsa, bu yönteme yapılan tüm çağrılar (ancak yöntemin kendisi değil) C# derleyicisi tarafından kaldırılır. Genellikle bu hata ayıklama (tanılama) amacıyla kullanılır.

* `[CallerMemberName]`. Bu öznitelik parametreler üzerinde kullanılabilir ve `System.Runtime.CompilerServices` ad alanında yaşar. Bu, başka bir yöntem çağıran yöntemin adını enjekte etmek için kullanılan bir özniteliktir. Bu genellikle çeşitli UI çerçevelerinde INotifyPropertyChanged uygularken 'sihirli dizeleri' ortadan kaldırmak için bir yol olarak kullanılır. Örneğin:

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

Yukarıdaki kodda, gerçek `"Name"` bir dize olması zorunda değilsiniz. Bu, yazım hatasıyla ilgili hataları önlemeye yardımcı olabilir ve aynı zamanda daha düzgün yeniden düzenleme/yeniden adlandırma sağlar.

## <a name="summary"></a>Özet

Öznitelikler C#'a bildirimsel güç getirir, ancak kodun meta-veri biçimidir ve kendi başlarına hareket etmezler.
