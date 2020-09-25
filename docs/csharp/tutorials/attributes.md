---
title: 'Öğretici: öznitelikleri kullanın-C #'
description: C# ' de özniteliklerin nasıl çalıştığını öğrenin.
author: mgroves
ms.technology: csharp-fundamentals
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: 4e2c0126d0920df18271f8889d8e117cd374d979
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174192"
---
# <a name="use-attributes-in-c"></a>C 'de öznitelikleri kullanma\#

Öznitelikler, bilgileri bildirimli bir şekilde kod ile ilişkilendirmenin bir yolunu sağlar. Ayrıca, çeşitli hedeflere uygulanabilen yeniden kullanılabilir bir öğe de sağlayabilir.

Özniteliği göz önünde bulundurun `[Obsolete]` . Bu sınıf, yapı, yöntem, Oluşturucu ve daha fazlasına uygulanabilir. Öğenin eski olduğunu _bildirir_ . Daha sonra bu özniteliği aramak için C# derleyicisine kadar, yanıt olarak bazı eylemler yapılır.

Bu öğreticide, kodunuza nasıl öznitelik ekleneceği, kendi öznitelerinizi nasıl oluşturacağınız ve kullanacağınız ve .NET Core 'da yerleşik bazı özniteliklerin nasıl kullanılacağı gösterilir.

## <a name="prerequisites"></a>Önkoşullar

Makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir. Yükleme yönergelerini [.NET Core İndirmeleri](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz.
Bu uygulamayı Windows, Ubuntu Linux, macOS veya bir Docker kapsayıcısında çalıştırabilirsiniz.
En sevdiğiniz kod düzenleyicinizi yüklemeniz gerekir. Aşağıdaki açıklamalar açık kaynaklı, platformlar arası düzenleyici olan [Visual Studio Code](https://code.visualstudio.com/) kullanır. Bununla birlikte, rahat olan her türlü aracı kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulamayı oluşturma

Tüm araçları yüklemişseniz, yeni bir .NET Core uygulaması oluşturun. Komut satırı Oluşturucuyu kullanmak için, en sevdiğiniz kabukta aşağıdaki komutu yürütün:

`dotnet new console`

Bu komut, tam kemikler .NET Core proje dosyaları oluşturur. `dotnet restore`Bu projeyi derlemek için gereken bağımlılıkları geri yüklemek için yürütmeniz gerekir.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Programı yürütmek için kullanın `dotnet run` . Konsola "Hello, World" çıkışını görmeniz gerekir.

## <a name="how-to-add-attributes-to-code"></a>Koda öznitelikler ekleme

C# ' de, öznitelikler temel sınıftan devraldığı sınıflardır `Attribute` . Öğesinden devralan herhangi bir sınıf `Attribute` , diğer kod parçalarında "Tag" sıralaması olarak kullanılabilir.
Örneğin, adlı bir öznitelik vardır `ObsoleteAttribute` . Bu, kodun artık kullanılmıyor olduğunu ve artık kullanılmaması gerektiğini bildirmek için kullanılır. Bu özniteliği bir sınıfa, örneğin köşeli ayraçları kullanarak yerleştirebilirsiniz.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]

Sınıf çağrıldığında `ObsoleteAttribute` yalnızca kodda kullanılması gerektiğini unutmayın `[Obsolete]` . Bu, C# ' nin Izlediği bir kuraldır.
Seçeneğini belirlerseniz tam adı kullanabilirsiniz `[ObsoleteAttribute]` .

Bir sınıf kullanım dışı olarak işaretlenirken, *neden* kullanımdan kalktı ve/veya bunun yerine *ne tür* bir bilgi sağlamanız yararlı olur. Bunu, kullanılmayan özniteliğe bir String parametresi geçirerek yapın.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

Dize, tıpkı yazarken olduğu gibi bir oluşturucuya bağımsız değişken olarak geçirilir `ObsoleteAttribute` `var attr = new ObsoleteAttribute("some string")` .

Öznitelik oluşturucusuna yönelik parametreler basit türler/sabit değerler: `bool, int, double, string, Type, enums, etc` ve bu türlerin dizileri ile sınırlıdır.
Bir ifade veya değişken kullanamazsınız. Konumsal veya adlandırılmış parametrelerin kullanımı ücretsizdir.

## <a name="how-to-create-your-own-attribute"></a>Kendi öznitelerinizi oluşturma

Özniteliği oluşturmak, temel sınıftan devralma kadar basittir `Attribute` .

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Yukarıdaki gibi, artık `[MySpecial]` `[MySpecialAttribute]` kod tabanında başka bir öznitelik olarak (veya) kullanabilirsiniz.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

.NET temel sınıf kitaplığındaki öznitelikler `ObsoleteAttribute` , derleyicinin içindeki belirli davranışları tetikler. Ancak, oluşturduğunuz herhangi bir öznitelik yalnızca meta veri olarak davranır ve yürütülen öznitelik sınıfı içinde herhangi bir koda neden olmaz. Bu meta verileri kodunuzun başka bir yerinde (daha sonra öğreticide daha sonra) uygulamak sizin için önemlidir.

Burada izlemek için bir ' Gotcha ' bulunur. Yukarıda belirtildiği gibi, öznitelikleri kullanırken yalnızca belirli türlerin bağımsız değişken olarak geçirilmesine izin verilir. Ancak, bir öznitelik türü oluştururken, C# derleyicisi bu parametreleri oluşturmamak için bunu durdurmaz. Aşağıdaki örnekte, yalnızca iyi şekilde derlenen bir oluşturucuya sahip bir öznitelik oluşturduğdum.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Ancak, bu oluşturucuyu öznitelik söz dizimi ile kullanamazsınız.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

Yukarıdaki gibi derleyici hatasına neden olur `Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>Öznitelik kullanımını kısıtlama

Öznitelikler, bir dizi "hedef" üzerinde kullanılabilir. Yukarıdaki örneklerde bunları sınıflarda gösterilmektedir, ancak bunlar üzerinde de kullanılabilir:

* Bütünleştirilmiş Kod
* Sınıf
* Oluşturucu
* Temsilci
* Sabit listesi
* Olay
* Alan
* GenericParameter
* Arabirim
* Yöntem
* Modül
* Parametre
* Özellik
* ReturnValue
* Yapı

Bir öznitelik sınıfı oluşturduğunuzda, varsayılan olarak C#, bu özniteliği olası öznitelik hedeflerinin herhangi birinde kullanmanıza izin verir. Öznitelerinizi belirli hedeflere kısıtlamak isterseniz, bunu `AttributeUsageAttribute` öznitelik sınıfınıza kullanarak yapabilirsiniz. Bu, öznitelik üzerindeki bir özniteliği!

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Yukarıdaki özniteliği bir sınıf veya yapı olmayan bir şeye koymaya çalışırsanız, şu şekilde bir derleyici hatası alırsınız `Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Bir kod öğesine eklenen öznitelikleri kullanma

Öznitelikler meta veri olarak davranır. Dışarı hiçbir dışa zorlama olmadan aslında hiçbir şey yapmaz.

Öznitelikleri bulmak ve üzerinde işlem yapmak için, [yansıma](../programming-guide/concepts/reflection.md) genellikle gereklidir. Bu öğreticide yansıma derinlemesine bir savunma ele alınmayacak, ancak temel düşünce, yansımanın diğer kodu inceleyen C# dilinde kod yazmanıza olanak tanır.

Örneğin, bir sınıf hakkında bilgi almak için yansıma kullanabilirsiniz ( `using System.Reflection;` kodunuzun başını ekleyin):

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

Bu, şöyle bir şey yazdıracaktır: `The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Bir `TypeInfo` nesneniz (veya `MemberInfo` , `FieldInfo` vb.) olduktan sonra `GetCustomAttributes` yöntemini kullanabilirsiniz. Bu, nesnelerin bir koleksiyonunu döndürür `Attribute` .
Ayrıca, öğesini kullanabilir `GetCustomAttribute` ve bir öznitelik türü belirtebilirsiniz.

İşte `GetCustomAttributes` bir `MemberInfo` örneği üzerinde `MyClass` (daha önce gördük daha önce bir özniteliğe sahip olan bir `[Obsolete]` özniteliği) kullanılmasına bir örnek.

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

Bu işlem konsola yazdırılır: `Attribute on MyClass: ObsoleteAttribute` . Diğer öznitelikleri eklemeyi deneyin `MyClass` .

Bu nesnelerin geç örneği olduğunu unutmamak önemlidir `Attribute` . Diğer bir deyişle, veya kullanmanıza kadar bu, örneklenemez `GetCustomAttribute` `GetCustomAttributes` .
Bunlar her seferinde de örneklenmiştir. `GetCustomAttributes`Bir satırda iki kez çağrılması iki farklı örnek döndürür `ObsoleteAttribute` .

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Temel sınıf kitaplığındaki (BCL) ortak öznitelikler

Öznitelikler birçok araç ve çerçeve tarafından kullanılır. NUnit `[Test]` `[TestFixture]` , NUnit Test Çalıştırıcısı tarafından kullanılan ve gibi öznitelikleri kullanır. ASP.NET MVC gibi öznitelikleri kullanır `[Authorize]` ve MVC eylemleri üzerinde çapraz kesme sorunları gerçekleştirmek için bir eylem filtresi çerçevesi sağlar. [Postsharp](https://www.postsharp.net) , C# dilinde en boy yönelimli programlamaya izin vermek için öznitelik sözdizimini kullanır.

.NET Core temel sınıf kitaplıklarında yerleşik olarak bulunan bazı önemli öznitelikleri aşağıda verilmiştir:

* `[Obsolete]`. Bu bir tane Yukarıdaki örneklerde kullanılmıştır ve `System` ad alanında bulunur. Değişen kod tabanı hakkında bildirime dayalı belgeler sağlamak yararlıdır. Bir ileti bir dize biçiminde sağlanıyor ve bir derleyici uyarısına bir derleyici hatasına iletmek için başka bir Boolean parametresi kullanılabilir.

* `[Conditional]`. Bu öznitelik `System.Diagnostics` ad alanıdır. Bu öznitelik yöntemlere (veya öznitelik sınıflarına) uygulanabilir. Oluşturucuya bir dize geçirmeniz gerekir.
Bu dize bir `#define` yönergeyle eşleşmiyorsa, söz konusu metoda yapılan çağrılar (ancak yöntemin kendisi değil) C# derleyicisi tarafından kaldırılır. Genellikle bu, hata ayıklama (Tanılama) amaçlarıyla kullanılır.

* `[CallerMemberName]`. Bu öznitelik, parametrelerde kullanılabilir ve `System.Runtime.CompilerServices` ad alanında bulunabilir. Bu, başka bir yöntemi çağıran yöntemin adını eklemek için kullanılan bir özniteliktir. Bu, genellikle çeşitli kullanıcı arabirimi çerçevelerinde INotifyPropertyChanged uygularken ' sihirli dizeler ' ' i ortadan kaldırmanın bir yolu olarak kullanılır. Örneğin:

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

Yukarıdaki kodda, bir sabit dize olması gerekmez `"Name"` . Bu, typo ile ilgili hataları önlemeye yardımcı olabilir ve ayrıca daha yumuşak yeniden düzenleme/yeniden adlandırma sağlar.

## <a name="summary"></a>Özet

Öznitelikler, C# ' ye bildirim temelli bir değer getirir, ancak bunlar bir meta veri biçimidir ve kendilerine göre hareket ederler.
