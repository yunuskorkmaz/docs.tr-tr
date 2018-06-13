---
title: Öznitelikler - C#
description: C# ' ta öznitelikleri nasıl çalıştığını öğrenin.
author: mgroves
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: db6db50ac59e804225bdc11c435fef3d53fa685e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352701"
---
# <a name="using-attributes-in-c"></a>Öznitelikleri C# ile kullanma #

Öznitelikler bilgileri bildirim temelli bir yolla kod ile ilişkilendirmek için bir yol sağlar. Bunlar, çeşitli hedefleri için uygulanabilir yeniden kullanılabilir bir öğesi de sağlayabilirsiniz.

Göz önünde bulundurun `[Obsolete]` özniteliği. Sınıflar, yapılar, yöntemleri, Oluşturucular ve daha fazla bilgi için uygulanabilir. Bu _bildirir_ öğesi kullanılmıyor. Bu öznitelik için konum ve yanıt bazı eylemi yapmak için C# Derleyici kadar sonra olur.

Bu öğreticide, kodunuzu öznitelikleri ekleme, oluşturma ve kendi özniteliklerini kullanın ve .NET Core içinde yerleşik olan bazı öznitelikler kullanma giriş.

## <a name="prerequisites"></a>Önkoşullar
.NET core çalışmasına, makine Kurulum gerekir. Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.
Bu uygulama, Windows, Ubuntu Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz. Sık kullanılan Kod Düzenleyicisi'ni yüklemeniz gerekir. Kullanım aşağıda açıklamaları [Visual Studio Code](https://code.visualstudio.com/) platform Düzenleyicisi arası bir açık kaynak olduğu. Ancak, tanımanız ne olursa olsun araçları kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulama oluşturma

Tüm Araçlar yüklediniz, yeni bir .NET Core uygulaması oluşturun. Komut satırı Oluşturucu kullanmak için sık kullanılan Kabuğu'nda aşağıdaki komutu yürütün:

`dotnet new console`

Bu komut, .NET core proje dosyalarını temel oluşturur. Yürütme gerekecek `dotnet restore` bu projeyi derlemek için gerekli bağımlılıkların geri yüklemek için.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Programı çalıştırmak üzere kullanmadan `dotnet run`. "Hello, World" çıkışı konsola görmeniz gerekir.

## <a name="how-to-add-attributes-to-code"></a>Öznitelikleri için kod ekleme

C# ' ta sınıfından devralınan sınıflar öznitelikleridir `Attribute` temel sınıfı. Öğesinden devralınan herhangi bir sınıf `Attribute` diğer kod parçalarını "etiketi" bir tür kullanılabilir.
Örneğin, adlı bir öznitelik yok `ObsoleteAttribute`. Bu kodu kullanımdan kalkmıştır ve artık kullanılmaması göstermek için kullanılır. Köşeli ayraçlar kullanarak bu özniteliği bir sınıf örneği için yerleştirebilirsiniz.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]  

Sınıf çağırıldıktan unutmayın `ObsoleteAttribute`, yalnızca kullanmak gerekli olan `[Obsolete]` kod. Bu, C# izleyen bir kuraldır.
Tam adını kullanabilirsiniz `[ObsoleteAttribute]` seçerseniz.

Bir sınıf artık kullanılmıyor işaretleme, onu olarak bazı bilgiler sağlamak için iyi bir fikirdir *neden* eski olarak ve/veya *ne* kullanmayı. Bir dize parametresi için geçersiz öznitelik geçirerek bunu.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

Dize bağımsız değişkeni olarak geçirilmiş bir `ObsoleteAttribute` oluşturucusu, yazma gibi yalnızca `var attr = new ObsoleteAttribute("some string")`.

Bir öznitelik Oluşturucusu parametrelerinin basit türleri/değişmez değerleri için sınırlı: `bool, int, double, string, Type, enums, etc` ve bu türlerin dizileri.
Bir ifade veya değişkeni kullanamazsınız. Konumsal veya adlandırılmış parametreleri kullanmakta serbestsiniz.

## <a name="how-to-create-your-own-attribute"></a>Kendi özniteliğinizi oluşturma

Bir öznitelik oluşturma içinden devralma olarak basit `Attribute` temel sınıfı.

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Yukarıdaki ile artık kullanabilirim `[MySpecial]` (veya `[MySpecialAttribute]`) kod temeli herhangi bir yerinde bir öznitelik olarak.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

.NET temel sınıf kitaplığı'nda öznitelikleri ister `ObsoleteAttribute` derleyici içinde belirli davranışlarını tetikler. Ancak, oluşturduğunuz herhangi bir öznitelik yalnızca meta veri davranır ve yürütülmekte öznitelik sınıfı içinde herhangi bir kod neden değil. Bu, meta verilerin başka bir yerde, kodunuzda (daha ayrıntılı daha sonra öğreticide) hareket etmesine için hazır.

Yok 'sorunu' burada dikkat edilmesi gereken. Yukarıda belirtildiği gibi yalnızca belirli türleri öznitelikleri kullanırken bağımsız değişken olarak geçirilen izin verilmez. Ancak, bir öznitelik türü oluştururken, C# Derleyici bu parametreleri oluşturmak durdurmanız olmaz. İçinde aşağıdaki örnekte, t bir öznitelik, derlenen bir oluşturucu yalnızca ince oluşturuldu.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Ancak, bu oluşturucuyu özniteliği sözdizimiyle kullanamadı olacaktır.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

Yukarıdaki gibi derleyici hatası neden olur `Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>Öznitelik kullanımı kısıtlama

Öznitelikleri "hedefler" sayısına kullanılabilir. Yukarıdaki örneklerde sınıflarında göstermek, ancak üzerinde de kullanılabilir:

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
* ReturnValue
* Yapı

Varsayılan olarak bir öznitelik sınıfı oluşturduğunuzda, C# bu öznitelik olası öznitelik hedefleri hiçbirinde kullanmanıza olanak sağlar. Belirli hedeflere özniteliğinizi kısıtlamak istiyorsanız, kullanarak bunu yapabilirsiniz `AttributeUsageAttribute` özniteliği sınıfınızın. Bu, özniteliğin öznitelik sağ var!

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Yukarıdaki özniteliği bir sınıf veya yapı olmayan öğe üzerinde put çalışırsanız, gibi bir derleyici hatası alırsınız `Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Bir kod öğesine eklenen öznitelikler kullanma

Öznitelikleri meta veri davranır. Bazı dışa doğru zorla bunların herhangi bir şey gerçekte olmaz.

Bulma ve özniteliklerini temel hareket [yansıma](../programming-guide/concepts/reflection.md) genellikle gereklidir. Bu öğreticide ayrıntılı yansıma kapak çalışmaz, ancak temel düşünce yansıma kod C diğer kod inceleyen #'ta yazmanıza olanak sağlamasıdır.

Örneğin, bir sınıf hakkında bilgi almak için yansıma kullanabilirsiniz: 

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

Aşağıdakine benzer yazdırmak: `The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Bulduktan sonra bir `TypeInfo` nesne (veya bir `MemberInfo`, `FieldInfo`, vb.), kullanabileceğiniz `GetCustomAttributes` yöntemi. Bu bir koleksiyonunu döndürür `Attribute` nesneleri.
Aynı zamanda `GetCustomAttribute` ve bir öznitelik türü belirtin.

Kullanma örneği `GetCustomAttributes` üzerinde bir `MemberInfo` örnek `MyClass` (daha önce gördüğümüz olan bir `[Obsolete]` Bu öznitelikte).

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

Konsola yazdırma: `Attribute on MyClass: ObsoleteAttribute`. Diğer öznitelikleri eklemeyi deneyin `MyClass`.

Bu dikkate almak önemlidir bunlar `Attribute` nesnelerine ait örneklerin gevşek. Kullandığınız kadar diğer bir deyişle, bunlar oluşturulmasını olmaz `GetCustomAttribute` veya `GetCustomAttributes`.
Bunlar, ayrıca her zaman oluşturulur. Çağırma `GetCustomAttributes` arka arkaya iki kez iki farklı örnekleri döndürülecek `ObsoleteAttribute`.

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Ortak öznitelikler (BCL) temel sınıf kitaplığı'nda

Öznitelikler, birçok araçları ve çerçeveleri tarafından kullanılır. NUnit kullanır gibi özniteliklere `[Test]` ve `[TestFixture]` NUnit test Çalıştırıcısı tarafından kullanılır. ASP.NET MVC kullanır gibi özniteliklere `[Authorize]` ve çapraz kesme sorunları MVC eylemleri gerçekleştirmek için bir eylem filtresi çerçeve sağlar. [PostSharp](https://www.postsharp.net) en boy odaklı programlama C# izin vermek için öznitelik sözdizimini kullanır.

.NET Core temel sınıf kitaplıklara yerleşik birkaç önemli öznitelikleri şunlardır:

* `[Obsolete]`. Bunu Yukarıdaki örneklerde kullanılan ve yaşadığı `System` ad alanı. Değişen kod tabanını hakkında bildirim temelli belgeleri sağlamak kullanışlıdır. Bir ileti bir dize biçiminde sağlanabilir ve başka bir Boole parametresi için bir derleyici hatası derleyici uyarıdan ilerletmek için kullanılabilir.

* `[Conditional]`. Bu öznitelik bulunduğu `System.Diagnostics` ad alanı. Bu öznitelik yöntemleri (veya öznitelik sınıfları) uygulanabilir. Bir dize oluşturucuya geçmesi gerekir.
Eşleşen dize varsa bir `#define` yönerge, ardından o yöntemi (ancak yöntem kendisi değil) yapılan her çağrı C# Derleyici tarafından kaldırılacak. Genellikle bu hata ayıklama (tanılama) amacıyla kullanılır.

* `[CallerMemberName]`. Bu öznitelik parametreleri ve yaşamlarını içinde kullanılabilir `System.Runtime.CompilerServices` ad alanı. Bu, başka bir metot çağırmadan yöntemin adını eklemesine kullanılan bir özniteliğidir. Bu genellikle 'dizeleri Sihirli' ortadan kaldırmak için bir yol olarak kullanılan INotifyPropertyChanged içinde çeşitli UI çerçeve uygularken. Örneğin:

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

Yukarıdaki kod içinde bir hazır değer sahip olmak zorunda değildir `"Name"` dize. Bu yazım hatası ile ilgili hatalar önlenmesine yardımcı olabilir ve daha sorunsuz yeniden düzenleme/yeniden adlandırmak için de sağlar.

## <a name="summary"></a>Özet

Bildirim temelli güç öznitelikleri C# getirin. Ancak meta veri olarak kod biçimidir ve tek başına hareket yok.
