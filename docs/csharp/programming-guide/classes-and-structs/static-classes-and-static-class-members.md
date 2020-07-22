---
title: Statik sınıflar ve statik sınıf üyeleri-C# Programlama Kılavuzu
description: Statik sınıflar C# ' de başlatılamaz. Statik bir sınıfın üyelerine sınıf adının kendisini kullanarak erişirsiniz.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 4f187d772d2f2e4375fbe3cfdc8c48af691f1c7c
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863883"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Statik Sınıflar ve Statik Sınıf Üyeleri (C# Programlama Kılavuzu)

[Statik](../../language-reference/keywords/static.md) bir sınıf temelde statik olmayan bir sınıfla aynıdır, ancak bir fark vardır: statik bir sınıf örneği oluşturulamıyor. Diğer bir deyişle, sınıf türünde bir değişken oluşturmak için [New](../../language-reference/operators/new-operator.md) işlecini kullanamazsınız. Örnek değişkeni olmadığından, bir statik sınıfın üyelerine sınıf adının kendisini kullanarak erişirsiniz. Örneğin, ortak statik bir yöntemi adlı adlı bir statik sınıfınız varsa `UtilityClass` `MethodA` , yöntemi aşağıdaki örnekte gösterildiği gibi çağırın:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Statik bir sınıf, yalnızca giriş parametrelerinde çalışan yöntemlerin kümeleri için uygun bir kapsayıcı olarak kullanılabilir ve herhangi bir iç örnek alanı almak veya ayarlamak zorunda değildir. Örneğin, .NET sınıf kitaplığı 'nda statik <xref:System.Math?displayProperty=nameWithType> sınıf, sınıfının belirli bir örneğine özgü verileri depolamak veya almak için herhangi bir gereksinim olmadan matematik işlemleri gerçekleştiren yöntemler içerir <xref:System.Math> . Diğer bir deyişle, aşağıdaki örnekte gösterildiği gibi sınıf adını ve yöntem adını belirterek sınıfının üyelerini uygularsınız.  
  
```csharp  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
```  
  
 Tüm sınıf türlerinde olduğu gibi, bir statik sınıf için tür bilgisi, sınıfa başvuran program yüklendiğinde .NET çalışma zamanı tarafından yüklenir. Program, sınıf yüklendiğinde tam olarak belirtemez. Ancak, yüklenmesi ve alanları başlatılmış olması garantidir ve bu sınıfın, sınıf ilk kez bir kez başvurulmadan önce çağrılan statik Oluşturucusu çağırılır. Statik bir Oluşturucu yalnızca bir kez çağrılır ve programınızın bulunduğu uygulama etki alanının ömrü boyunca statik bir sınıf bellekte kalır.  
  
> [!NOTE]
> Yalnızca tek bir örneğinin oluşturulmasına izin veren statik olmayan bir sınıf oluşturmak için, bkz. [C# ' de](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316%28v=pandp.10%29)tek bir örnek uygulama.  
  
 Aşağıdaki liste, bir statik sınıfın ana özelliklerini sağlar:  
  
- Yalnızca statik üyeleri içerir.  
  
- Örneği oluşturulamıyor.  
  
- Mühürlü.  
  
- [Örnek oluşturucular](./instance-constructors.md)içeremez.  
  
 Statik sınıf oluşturmak, bu nedenle temelde yalnızca statik üyeler ve özel bir Oluşturucu içeren bir sınıf oluşturma ile aynıdır. Özel Oluşturucu sınıfın oluşturulmasını engeller. Statik sınıf kullanmanın avantajı, derleyicinin yanlışlıkla hiç örnek üye bulunmadığından emin olmak için denetim yapamamasına olanak sağlar. Derleyici, bu sınıfın örneklerinin oluşturuoluşturulamadığı garantisi alacak.  
  
 Statik sınıflar mühürlenmiş ve bu nedenle devralınamaz. Dışında herhangi bir sınıftan devralınabilir <xref:System.Object> . Statik sınıflar bir örnek oluşturucu içeremez. Ancak, bir statik Oluşturucu içerebilirler. Statik olmayan sınıflar Ayrıca, sınıf önemsiz olmayan başlatma gerektiren statik üyeler içeriyorsa statik bir Oluşturucu tanımlamalıdır. Daha fazla bilgi için bkz. [statik oluşturucular](./static-constructors.md).  
  
## <a name="example"></a>Örnek  
 Aşağıda, sıcaklığın Fahrenhayt 'e ve Fahrenhayt 'e kadar olan iki yöntem içeren bir statik sınıfa örnek verilmiştir:  
  
 [!code-csharp[csProgGuideObjects#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#31)]  
  
## <a name="static-members"></a>Statik Üyeler  
 Statik olmayan bir sınıf statik yöntemler, alanlar, özellikler veya olaylar içerebilir. Statik üye, sınıfın bir örneği oluşturulmasa bile bir sınıf üzerinde çağrılabilir. Statik üyeye, örnek adı değil, her zaman sınıf adı tarafından erişilir. Statik üyenin yalnızca bir kopyası, sınıfının kaç örneğinin oluşturulduğuna bakılmaksızın vardır. Statik yöntemler ve özellikler, kendi kapsayıcı türündeki statik olmayan alanlara ve olaylara erişemez ve açıkça bir yöntem parametresine geçirilmediği takdirde herhangi bir nesnenin örnek değişkenine erişemez.  
  
 Statik olmayan bir sınıfı bazı statik üyelere bildirmek daha tipik bir deyişle, bir sınıfın tamamını statik olarak bildirmek daha normaldir. Statik alanların iki ortak kullanımı, örneği oluşturulmuş nesne sayısının sayısını tutmak veya tüm örnekler arasında paylaşılması gereken bir değeri depolamak için kullanılır.  
  
 Statik yöntemler, sınıfın herhangi bir örneğine değil, sınıfına ait olduğundan aşırı yüklenebilir ancak geçersiz kılınmaz.  
  
 Bir alan olarak bildirilemez olsa da `static const` , bir [const](../../language-reference/keywords/const.md) alanı, davranışında temelde statiktir. Tür örneklerine değil, türüne aittir. Bu nedenle, `const` alanlara `ClassName.MemberName` statik alanlar için kullanılan aynı gösterim kullanılarak erişilebilir. Nesne örneği gerekli değil.  
  
 C# statik yerel değişkenleri (yani, yöntem kapsamında belirtilen değişkenleri) desteklemez.  
  
 `static`Aşağıdaki örnekte gösterildiği gibi, üyenin dönüş türünden önce anahtar sözcüğünü kullanarak statik sınıf üyeleri bildirirsiniz:  
  
 [!code-csharp[csProgGuideObjects#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#29)]  
  
 Statik üyeler, statik üyeye ilk kez erişilmeden ve statik oluşturucu bir tane varsa, önce başlatılır. Statik sınıf üyesine erişmek için, aşağıdaki örnekte gösterildiği gibi, üyenin konumunu belirtmek için değişken adı yerine sınıfın adını kullanın:  
  
 [!code-csharp[csProgGuideObjects#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#30)]  
  
 Sınıfınız statik alanlar içeriyorsa, sınıfı yüklendiğinde bunları başlatan bir statik Oluşturucu sağlayın.  
  
 Statik bir yönteme yapılan çağrı, Microsoft ara dili (MSIL) içinde bir çağrı yönergesi oluşturur, ancak bir örnek yöntemine yapılan çağrı bir yönerge oluşturur; `callvirt` Bu da null nesne başvurularını denetler. Ancak, ikisi arasındaki performans farkı çoğu zaman önemli değildir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [statik sınıflar](~/_csharplang/spec/classes.md#static-classes) ve [statik ve örnek üyeleri](~/_csharplang/spec/classes.md#static-and-instance-members) bölümüne bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [static](../../language-reference/keywords/static.md)
- [Sınıflar](./classes.md)
- [sınıfı](../../language-reference/keywords/class.md)
- [Statik Oluşturucular](./static-constructors.md)
- [Örnek Oluşturucuları](./instance-constructors.md)
