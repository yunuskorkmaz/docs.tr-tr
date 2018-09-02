---
title: Öznitelikleri - C#
description: C# dilinde öznitelikleri nasıl çalıştığını öğrenin.
author: mgroves
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: db6db50ac59e804225bdc11c435fef3d53fa685e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43390525"
---
# <a name="using-attributes-in-c"></a>Öznitelikleri kullanarak C# #

Öznitelikler bilgileri, bildirim temelli bir şekilde kod ile ilişkilendirmek için bir yol sağlar. Bunlar, çeşitli hedefleri için uygulanabilir yeniden kullanılabilir bir öğe de sağlayabilirsiniz.

Göz önünde bulundurun `[Obsolete]` özniteliği. Sınıflar, yapılar, yöntemleri, Oluşturucular ve daha fazla bilgi için uygulanabilir. Bunu _bildirir_ öğe kullanılmıyor. Bu öznitelik için bakın ve bazı yanıt eylemi yapmak için C# Derleyici kadar sonra olur.

Bu öğreticide, kodunuzu öznitelikleri ekleme, oluşturma ve kendi öznitelikleri ve .NET Core ile oluşturulan bazı öznitelikleri kullanmayla izleyeceksiniz.

## <a name="prerequisites"></a>Önkoşullar
.NET core çalıştırmak için makinenizi ayarlamak gerekir. Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.
Bu uygulama, Windows, Ubuntu Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz. Sık kullandığınız Kod Düzenleyicisi'ni yüklemeniz gerekir. Aşağıdaki tanımlamalar [Visual Studio Code](https://code.visualstudio.com/) açık kaynaklı, çapraz platform Düzenleyicisi olduğu. Ancak, rahat sevdiğiniz araçları kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulama oluşturma

Tüm Araçlar'ı yüklediğinize göre yeni bir .NET Core uygulaması oluşturun. Komut satırı Oluşturucu kullanmak için sık kullanılan shell'de aşağıdaki komutu yürütün:

`dotnet new console`

Bu komut, .NET core proje dosyaları temel oluşturur. Yürütmek ihtiyacınız olacak `dotnet restore` bu projeyi derlemek için gerekli bağımlılıkların geri yüklemek için.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Programı çalıştırmak üzere kullanmadan `dotnet run`. "Hello, World" konsol çıktısı için görmeniz gerekir.

## <a name="how-to-add-attributes-to-code"></a>Öznitelikler için kod ekleme

C# ', devralınan sınıflar öznitelikleridir `Attribute` temel sınıfı. Devralınan herhangi bir sınıf `Attribute` kod parçalarını "etiket" bir tür kullanılabilir.
Örneğin, adlı bir öznitelik yoktur `ObsoleteAttribute`. Bu, kodu kullanımdan kalkmıştır ve artık kullanılmamalıdır göstermek için kullanılır. Köşeli ayraçlar kullanarak, bu öznitelik bir sınıf örneği için yerleştirebilirsiniz.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]  

Sınıf çağırıldıktan unutmayın `ObsoleteAttribute`, yalnızca kullanmak gerekli olan `[Obsolete]` kod. Bu C# izleyen bir kuraldır.
Tam adını kullanabilirsiniz `[ObsoleteAttribute]` seçerseniz.

Eski bir sınıfı işaretlemek, bu olarak bazı bilgileri sağlamak için iyi bir fikirdir *neden* eski ve/veya *ne* yerine kullanılacak. Bir dize parametresi için geçersiz öznitelik geçirerek bunu.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

Dize bağımsız değişkeni olarak geçirilir bir `ObsoleteAttribute` oluşturucusu, sizin için yazar gibi yalnızca `var attr = new ObsoleteAttribute("some string")`.

Öznitelik oluşturucuda parametre basit türleri/değişmez değerleri için sınırlı: `bool, int, double, string, Type, enums, etc` ve bu türlerin dizileri.
Bir ifade veya bir değişkeni kullanamazsınız. Konumsal veya adlandırılmış parametreleri kullanmak ücretsizdir.

## <a name="how-to-create-your-own-attribute"></a>Kendi öznitelik oluşturma

Öznitelik oluşturma dan devralan olarak basit `Attribute` temel sınıfı.

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Yukarıdaki ile artık kullanabilirim `[MySpecial]` (veya `[MySpecialAttribute]`) bir öznitelik kod tabanı olarak başka bir yerde.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

.NET temel sınıf kitaplığı'nda öznitelikleri ister `ObsoleteAttribute` derleyici içinde belirli davranışları tetikleyin. Ancak, oluşturduğunuz herhangi bir öznitelik, yalnızca meta veri olarak davranır ve yürütülmekte olan öznitelik sınıfı içinde herhangi bir kod oluşturmaz. Kodunuzu (daha fazla bilgi, öğreticinin ilerleyen bölümlerinde) içindeki başka bir yerde meta verilerin üzerinde işlem size aittir.

Var. 'sorunu' burada dikkat edilmesi gereken Yukarıda belirtildiği gibi yalnızca belirli türlerini öznitelikler kullanıldığında bağımsız değişken olarak geçirilmesine izin verilmez. Ancak, bir öznitelik türü oluştururken, C# derleyicisi, bu parametreleri oluşturmaktan durdurmaz. İçinde aşağıdaki örnekte, bir öznitelik derleyen bir oluşturucuyla düzgün oluşturdum.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Bununla birlikte, öznitelik sözdizimi ile bu oluşturucuyu kullanarak mümkün olmayacaktır.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

Yukarıdaki gibi bir derleyici hatasına neden olur `Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>Öznitelik kullanımı kısıtlama

Öznitelikler "hedef" bir dizi üzerinde kullanılabilir. Yukarıdaki örneklerde sınıflarında göstermek, ancak bunlar üzerinde de kullanılabilir:

* Derleme
* örneği
* Oluşturucu
* Temsilci
* Enum
* Olay
* Alan
* GenericParameter
* Arabirim
* Yöntem
* Modül
* Parametre
* Özellik
* returnValue
* Yapı

Varsayılan olarak bir öznitelik sınıfı oluşturduğunuzda, C#, bu öznitelik tüm olası öznitelik hedefleri kullanmanıza olanak sağlar. Belirli bir hedefe özniteliğinizi kısıtlamak istiyorsanız, bunu kullanarak yapabilirsiniz `AttributeUsageAttribute` özniteliği sınıfınızın. Bu, bir özniteliğin bir öznitelik sağ var!

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Yukarıdaki özniteliği bir sınıf veya yapı değil şeye koymak çalışırsanız, gibi derleyici bir hata alırsınız. `Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Ekli bir kod öğesi için öznitelikleri kullanma

Öznitelik meta veri olarak davranır. Bazı dışa doğru zorla, bunlar gerçekten herhangi bir şey olmaz.

Bul ve öznitelikleri üzerinde işlem yapma [yansıma](../programming-guide/concepts/reflection.md) genellikle gereklidir. Bu öğreticide ayrıntılı yansıma kapsayan olmaz, ancak temel yansıma diğer kodu inceleyen #c dilinde kod yazmanızı sağlayan uygulamadır.

Örneğin, bir sınıf hakkında bilgi almak için yansıma kullanabilirsiniz: 

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

Bu, aşağıdakine benzer çıkış yazdırır: `The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Sonra bir `TypeInfo` nesnesi (veya `MemberInfo`, `FieldInfo`, vb.), kullanabileceğiniz `GetCustomAttributes` yöntemi. Bu bir koleksiyonunu döndürür `Attribute` nesneleri.
Ayrıca `GetCustomAttribute` ve bir öznitelik türü belirtin.

Kullanımının bir örneği aşağıda verilmiştir `GetCustomAttributes` üzerinde bir `MemberInfo` örnek `MyClass` (daha önce gördüğümüz sahip bir `[Obsolete]` üzerindeki özniteliği).

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

Konsola yazdıracak: `Attribute on MyClass: ObsoleteAttribute`. Diğer öznitelikler için eklemeyi deneyin `MyClass`.

Dikkat etmeniz önemlidir bu `Attribute` nesnelerine ait örneklerin gevşek. Kullandığınız kadar diğer bir deyişle, bunlar örneği olmaz `GetCustomAttribute` veya `GetCustomAttributes`.
Ayrıca her zaman örneği oluşturulur. Çağırma `GetCustomAttributes` arka arkaya iki kez iki farklı örneklerini döndürür `ObsoleteAttribute`.

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Temel sınıf kitaplığı (BCL) ortak öznitelikleri

Öznitelikler, birçok araç ve çerçeve tarafından kullanılır. NUnit gibi öznitelikleri kullanır `[Test]` ve `[TestFixture]` NUnit test Çalıştırıcısı tarafından kullanılır. ASP.NET MVC kullanır gibi öznitelikleri `[Authorize]` ve geniş kapsamlı kritik konular MVC eylemleri gerçekleştirmek için bir eylem filtre framework sağlar. [PostSharp](https://www.postsharp.net) açı yönelimli programlama C# ' ta izin vermek için öznitelik sözdizimini kullanır.

.NET Core temel sınıf kitaplığına yerleşik birkaç önemli öznitelikleri şunlardır:

* `[Obsolete]`. Bu, Yukarıdaki örneklerde kullanılan ve kendini `System` ad alanı. Bildirim temelli belgelerine değişen bir kod temeli sağlamak kullanışlıdır. Bir dize biçiminde bir ileti sağlanabilir ve başka bir Boole parametresi için bir derleyici hatası derleyici uyarıdan ilerletmek için kullanılabilir.

* `[Conditional]`. Bu öznitelik bulunduğu `System.Diagnostics` ad alanı. Bu öznitelik, yöntemler (veya öznitelik sınıflarında) uygulanabilir. Oluşturucuya bir dize geçmesi gerekir.
Eşleşme dize, bir `#define` yönergesi, ardından bu yöntem (ancak yöntemin kendisi değil) yapılan her çağrı C# derleyicisi tarafından kaldırılacak. Genellikle bu hata ayıklama (tanılama) amacıyla kullanılır.

* `[CallerMemberName]`. Bu öznitelik parametreleri ve canlı kullanılabilir `System.Runtime.CompilerServices` ad alanı. Başka bir yöntemi çağıran yöntemin adı ekleme için kullanılan bir özniteliği budur. Bu genellikle bir şekilde 'dizeleri Sihirli' ortadan kaldırmak için kullanılan çeşitli UI çerçeveleri alanında INotifyPropertyChanged uygularken. Örneğin:

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

Yukarıdaki kodda, bir sabit değer olan gerekmez `"Name"` dize. Bu, yazım hatası ile ilgili hataları önlemeye yardımcı olabilir ve daha sorunsuz yükseltmelere yeniden düzenleme/yeniden adlandırmak için de sağlar.

## <a name="summary"></a>Özet

Bildirim temelli güç öznitelikleri C# ' tan getirin. Ancak bir kod meta veri olarak biçimindedir ve kendileri tarafından harekete.
