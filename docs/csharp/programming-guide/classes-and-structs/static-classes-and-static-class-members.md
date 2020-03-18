---
title: Statik Sınıflar ve Statik Sınıf Üyeleri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 7add512b262afbabe996f752c083566a2c394dfd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705437"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Statik Sınıflar ve Statik Sınıf Üyeleri (C# Programlama Kılavuzu)

[Statik](../../language-reference/keywords/static.md) bir sınıf temelde statik olmayan bir sınıfla aynıdır, ancak bir fark vardır: statik bir sınıf anında kullanılamaz. Başka bir deyişle, sınıf türünden bir değişken oluşturmak için [yeni](../../language-reference/operators/new-operator.md) işleci kullanamazsınız. Örnek değişken olmadığından, sınıf adının kendisini kullanarak statik sınıfın üyelerine erişebilirsiniz. Örneğin, adlandırılmış `UtilityClass` bir statik sınıfıniz varsa, buna `MethodA`aşağıdaki örnekte gösterildiği gibi çağrıbilirsiniz:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Statik bir sınıf, giriş parametreleri üzerinde çalışan ve herhangi bir iç örnek alanını almak veya ayarlamak zorunda olmayan yöntem kümeleri için uygun bir kapsayıcı olarak kullanılabilir. Örneğin, .NET Framework Class Kitaplığı'nda statik <xref:System.Math?displayProperty=nameWithType> sınıf, <xref:System.Math> sınıfın belirli bir örneğine özgü verileri depolamaveya alma gereksinimi olmadan matematiksel işlemleri gerçekleştiren yöntemler içerir. Diğer bir deyişle, aşağıdaki örnekte gösterildiği gibi sınıf adını ve yöntem adını belirterek sınıf üyelerini uygularsınız.  
  
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
  
 Tüm sınıf türlerinde olduğu gibi, statik bir sınıfın tür bilgileri,.NET Framework ortak dil çalışma zamanı (CLR) tarafından sınıfa başvurulan program yüklendiğinde yüklenir. Program sınıfın tam olarak ne zaman yüklendiğini belirtemez. Ancak, programda ilk kez sınıfbaşvurulmadan önce, yükleme ve alanlarının başlatılması ve statik oluşturucusu çağrılması garanti edilir. Statik bir oluşturucu yalnızca bir kez çağrılır ve statik bir sınıf, programınızın bulunduğu uygulama etki alanının ömrü boyunca bellekte kalır.  
  
> [!NOTE]
> Yalnızca bir örneğinin oluşturulmasına izin veren statik olmayan bir sınıf oluşturmak için [bkz.](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316%28v=pandp.10%29)  
  
 Aşağıdaki liste statik bir sınıfın ana özelliklerini sağlar:  
  
- Yalnızca statik üyeler içerir.  
  
- Anlık olarak yapılamaz.  
  
- Mühürlü.  
  
- Örnek [Oluşturucular](./instance-constructors.md)içeremez.  
  
 Bu nedenle statik bir sınıf oluşturmak temelde yalnızca statik üyeler ve özel bir oluşturucu içeren bir sınıf oluşturmakla aynıdır. Özel bir oluşturucu sınıfın anlık olmasını engeller. Statik bir sınıf kullanmanın avantajı, derleyicinin hiçbir örnek üyenin yanlışlıkla eklenmediğinden emin olmak için denetlemesidir. Derleyici, bu sınıfın örneklerinin oluşturulamayacağını garanti eder.  
  
 Statik sınıflar mühürlenir ve bu nedenle devralınamaz. Onlar dışında <xref:System.Object>herhangi bir sınıftan miras olamaz. Statik sınıflar örnek oluşturucu içeremez; ancak statik bir oluşturucu içerebilirler. Non-statik sınıflar da bir statik oluşturucu tanımlamak gerekir sınıf önemsiz olmayan başlatma gerektiren statik üyeler içeriyorsa. Daha fazla bilgi için Statik [Oluşturucular'a](./static-constructors.md)bakın.  
  
## <a name="example"></a>Örnek  
 Sıcaklığı Santigrat'tan Fahrenhayt'a ve Fahrenhayt'tan Santigrat'a dönüştüren iki yöntem içeren statik bir sınıf örneği aşağıda verilmiştir:  
  
 [!code-csharp[csProgGuideObjects#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#31)]  
  
## <a name="static-members"></a>Statik Üyeler  
 Statik olmayan bir sınıf statik yöntemler, alanlar, özellikler veya olaylar içerebilir. Statik üye, sınıfın hiçbir örneği oluşturulmasa bile bir sınıfta çağrılabilir. Statik üyeye her zaman örnek adı değil, sınıf adı tarafından erişilir. Sınıfın kaç örneği oluşturulduğundan bağımsız olarak statik bir üyenin yalnızca bir kopyası vardır. Statik yöntemler ve özellikler, içeren türünde statik olmayan alanlara ve olaylara erişemez ve yöntem parametresinde açıkça geçilmediği sürece herhangi bir nesnenin örnek değişkenine erişemezler.  
  
 Tüm bir sınıfı statik olarak bildirmektense, bazı statik üyelerle statik olmayan bir sınıfı bildirmek daha tipiktir. Statik alanların iki yaygın kullanımı, anında alınan nesne sayısının sayısını tutmak veya tüm örnekler arasında paylaşılması gereken bir değeri depolamak içindir.  
  
 Statik yöntemler, sınıfın herhangi bir örneğine değil, sınıfa ait olduğundan aşırı yüklenebilir, ancak geçersiz kılınabilir.  
  
 Bir alan olarak `static const`bildirilemese de, [const](../../language-reference/keywords/const.md) alan aslında davranışında statiktir. Türe ait, tür örneklerine değil. Bu nedenle, const alanlara statik `ClassName.MemberName` alanlar için kullanılan aynı gösterim kullanılarak erişilebilir. Nesne örneği gerekmez.  
  
 C# statik yerel değişkenleri (yöntem kapsamında bildirilen değişkenler) desteklemez.  
  
 Aşağıdaki örnekte gösterildiği gibi, üyenin `static` dönüş türünden önce anahtar sözcüğü kullanarak statik sınıf üyelerini beyan emzmiş olursunuz:  
  
 [!code-csharp[csProgGuideObjects#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#29)]  
  
 Statik üyeye ilk kez erişilmeden önce ve statik yapıcı dan önce statik üyeler ekime denilir. Statik bir sınıf üyesine erişmek için, aşağıdaki örnekte gösterildiği gibi, üyenin konumunu belirtmek için değişken adı yerine sınıfın adını kullanın:  
  
 [!code-csharp[csProgGuideObjects#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#30)]  
  
 Sınıfınız statik alanlar içeriyorsa, sınıf yüklendiğinde bunları başlatifleştiren statik bir oluşturucu sağlayın.  
  
 Statik bir yönteme yapılan çağrı, Microsoft ara dilinde (MSIL) bir çağrı yönergesi oluştururken, örnek yöntemine yapılan bir çağrı, boş nesne başvurularını da denetleyen bir `callvirt` yönerge oluşturur. Ancak, çoğu zaman ikisi arasındaki performans farkı önemli değildir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Statik sınıflar](~/_csharplang/spec/classes.md#static-classes) ve Statik ve [örnek üyelere](~/_csharplang/spec/classes.md#static-and-instance-members) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Statik](../../language-reference/keywords/static.md)
- [Sınıflar](./classes.md)
- [Sınıfı](../../language-reference/keywords/class.md)
- [Statik Oluşturucular](./static-constructors.md)
- [Örnek Oluşturucuları](./instance-constructors.md)
