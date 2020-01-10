---
title: Statik sınıflar ve statik sınıf üyeleri- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 7add512b262afbabe996f752c083566a2c394dfd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705437"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Statik Sınıflar ve Statik Sınıf Üyeleri (C# Programlama Kılavuzu)

[Statik](../../language-reference/keywords/static.md) bir sınıf temelde statik olmayan bir sınıfla aynıdır, ancak bir fark vardır: statik bir sınıf örneği oluşturulamıyor. Diğer bir deyişle, sınıf türünde bir değişken oluşturmak için [New](../../language-reference/operators/new-operator.md) işlecini kullanamazsınız. Örnek değişkeni olmadığından, bir statik sınıfın üyelerine sınıf adının kendisini kullanarak erişirsiniz. Örneğin, `MethodA`adlı ortak bir statik yöntemi olan `UtilityClass` adlı statik bir sınıfınız varsa, aşağıdaki örnekte gösterildiği gibi yöntemi çağırın:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Statik bir sınıf, yalnızca giriş parametrelerinde çalışan yöntemlerin kümeleri için uygun bir kapsayıcı olarak kullanılabilir ve herhangi bir iç örnek alanı almak veya ayarlamak zorunda değildir. Örneğin, .NET Framework sınıf kitaplığında statik <xref:System.Math?displayProperty=nameWithType> sınıfı, <xref:System.Math> sınıfının belirli bir örneğine özgü verileri depolamak veya almak için herhangi bir gereksinim olmadan matematik işlemleri gerçekleştiren yöntemler içerir. Diğer bir deyişle, aşağıdaki örnekte gösterildiği gibi sınıf adını ve yöntem adını belirterek sınıfının üyelerini uygularsınız.  
  
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
  
 Tüm sınıf türlerinde olduğu gibi, bir statik sınıfa ait tür bilgileri, sınıfa başvuran program yüklendiğinde .NET Framework ortak dil çalışma zamanı (CLR) tarafından yüklenir. Program, sınıf yüklendiğinde tam olarak belirtemez. Ancak, yüklenmesi ve alanları başlatılmış olması garantidir ve bu sınıfın, sınıf ilk kez bir kez başvurulmadan önce çağrılan statik Oluşturucusu çağırılır. Statik bir Oluşturucu yalnızca bir kez çağrılır ve programınızın bulunduğu uygulama etki alanının ömrü boyunca statik bir sınıf bellekte kalır.  
  
> [!NOTE]
> Yalnızca tek bir örneğinin oluşturulmasına izin veren statik olmayan bir sınıf oluşturmak için, bkz. [tek Içinde C#uygulama ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316%28v=pandp.10%29).  
  
 Aşağıdaki liste, bir statik sınıfın ana özelliklerini sağlar:  
  
- Yalnızca statik üyeleri içerir.  
  
- Örneği oluşturulamıyor.  
  
- Mühürlü.  
  
- [Örnek oluşturucular](./instance-constructors.md)içeremez.  
  
 Statik sınıf oluşturmak, bu nedenle temelde yalnızca statik üyeler ve özel bir Oluşturucu içeren bir sınıf oluşturma ile aynıdır. Özel Oluşturucu sınıfın oluşturulmasını engeller. Statik sınıf kullanmanın avantajı, derleyicinin yanlışlıkla hiç örnek üye bulunmadığından emin olmak için denetim yapamamasına olanak sağlar. Derleyici, bu sınıfın örneklerinin oluşturuoluşturulamadığı garantisi alacak.  
  
 Statik sınıflar mühürlenmiş ve bu nedenle devralınamaz. <xref:System.Object>dışında herhangi bir sınıftan devralınabilir. Statik sınıflar bir örnek oluşturucu içeremez; Ancak, bir statik Oluşturucu içerebilirler. Statik olmayan sınıflar Ayrıca, sınıf önemsiz olmayan başlatma gerektiren statik üyeler içeriyorsa statik bir Oluşturucu tanımlamalıdır. Daha fazla bilgi için bkz. [statik oluşturucular](./static-constructors.md).  
  
## <a name="example"></a>Örnek  
 Aşağıda, sıcaklığın Fahrenhayt 'e ve Fahrenhayt 'e kadar olan iki yöntem içeren bir statik sınıfa örnek verilmiştir:  
  
 [!code-csharp[csProgGuideObjects#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#31)]  
  
## <a name="static-members"></a>Statik Üyeler  
 Statik olmayan bir sınıf statik yöntemler, alanlar, özellikler veya olaylar içerebilir. Statik üye, sınıfın bir örneği oluşturulmasa bile bir sınıf üzerinde çağrılabilir. Statik üyeye, örnek adı değil, her zaman sınıf adı tarafından erişilir. Statik üyenin yalnızca bir kopyası, sınıfının kaç örneğinin oluşturulduğuna bakılmaksızın vardır. Statik yöntemler ve özellikler, kendi kapsayıcı türündeki statik olmayan alanlara ve olaylara erişemez ve bir yöntem parametresine açıkça geçirilmediği takdirde herhangi bir nesnenin örnek değişkenine erişemez.  
  
 Statik olmayan bir sınıfı bazı statik üyelere bildirmek daha tipik bir deyişle, bir sınıfın tamamını statik olarak bildirmek daha normaldir. Statik alanların iki ortak kullanımı, örneği oluşturulmuş nesne sayısının sayısını tutmak veya tüm örnekler arasında paylaşılması gereken bir değeri depolamak için kullanılır.  
  
 Statik yöntemler, sınıfın herhangi bir örneğine değil, sınıfına ait olduğundan aşırı yüklenebilir ancak geçersiz kılınmaz.  
  
 Bir alan `static const`olarak bildirilemez olsa da, bir [const](../../language-reference/keywords/const.md) alanı, davranışında temelde statiktir. Tür örneklerine değil, türüne aittir. Bu nedenle, const alanlarına statik alanlar için kullanılan `ClassName.MemberName` gösterimi kullanılarak erişilebilir. Nesne örneği gerekli değil.  
  
 C#statik yerel değişkenleri desteklemez (Yöntem kapsamında belirtilen değişkenler).  
  
 Aşağıdaki örnekte gösterildiği gibi, üyenin dönüş türünden önce `static` anahtar sözcüğünü kullanarak statik sınıf üyeleri bildirirsiniz:  
  
 [!code-csharp[csProgGuideObjects#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#29)]  
  
 Statik üyeler, statik üyeye ilk kez erişilmeden ve statik oluşturucu bir tane varsa, önce başlatılır. Statik sınıf üyesine erişmek için, aşağıdaki örnekte gösterildiği gibi, üyenin konumunu belirtmek için değişken adı yerine sınıfın adını kullanın:  
  
 [!code-csharp[csProgGuideObjects#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#30)]  
  
 Sınıfınız statik alanlar içeriyorsa, sınıfı yüklendiğinde bunları başlatan bir statik Oluşturucu sağlayın.  
  
 Statik bir yönteme yapılan çağrı, Microsoft ara dili (MSIL) içinde bir çağrı yönergesi oluşturur, ancak bir örnek yöntemine yapılan çağrı bir `callvirt` yönerge oluşturur ve bu da null nesne başvurularını denetler. Ancak, ikisi arasındaki performans farkı çoğu zaman önemli değildir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için, [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [statik sınıflar](~/_csharplang/spec/classes.md#static-classes) ve [statik ve örnek üyeleri](~/_csharplang/spec/classes.md#static-and-instance-members) bölümüne bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [static](../../language-reference/keywords/static.md)
- [Sınıflar](./classes.md)
- [class](../../language-reference/keywords/class.md)
- [Statik Oluşturucular](./static-constructors.md)
- [Örnek Oluşturucuları](./instance-constructors.md)
