---
title: Statik sınıflar ve statik sınıf üyeleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 98d697aa7f4fa839b41509244993ced195730fdb
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585933"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Statik Sınıflar ve Statik Sınıf Üyeleri (C# Programlama Kılavuzu)
A [statik](../../../csharp/language-reference/keywords/static.md) sınıfı, temel bir statik olmayan sınıf ile aynı, ancak bir fark vardır: bir statik sınıfın örneği oluşturulamıyor. Diğer bir deyişle, kullanamazsınız [yeni](../../../csharp/language-reference/keywords/new.md) sınıf türünde bir değişken oluşturmak için anahtar sözcüğü. Hiçbir örnek değişken olduğundan, bir statik sınıf üyeleri sınıf adı'ı kullanarak erişir. Örneğin, bir statik sınıflar varsa adlı `UtilityClass` adlı genel statik bir yöntemi olan `MethodA`, aşağıdaki örnekte gösterildiği gibi yöntemi çağırın:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Statik sınıf yalnızca giriş parametrelerini üzerinde çalışır ve alınacak veya ayarlanacak herhangi bir dahili örnek alan olmayan yöntemler kümesi için uygun bir kapsayıcı olarak kullanılabilir. Örneğin, .NET Framework sınıf kitaplığı, statik olarak <xref:System.Math?displayProperty=nameWithType> sınıfı içeren depolamak veya belirli bir örneği için benzersiz olan veri almak için herhangi bir gereksinim olmadan matematiksel işlemler gerçekleştiren yöntemler <xref:System.Math> sınıfı. Diğer bir deyişle, sınıf üyeleri sınıf adı ve yöntem adını belirterek aşağıdaki örnekte gösterildiği gibi uygulayın.  
  
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
  
 Tüm sınıf türleri ile olduğu gibi bir statik sınıf için tür bilgisi sınıfı başvuran program yüklendiğinde .NET Framework ortak dil çalışma zamanı tarafından (CLR) yüklenir. Program, tam olarak ne zaman sınıfı yüklenen belirtemezsiniz. Ancak, yüklenecek ve başlatılmış kendi alanlarına ve sınıf programınızı ilk kez başvuruluyor önce çağırılır, statik Oluşturucu sağlanır. Statik Oluşturucu yalnızca bir kez çağrılır ve statik sınıf programınızı bulunduğu uygulama etki alanı ömrü boyunca bellekte kalır.  
  
> [!NOTE]
>  Oluşturulacak kendisi yalnızca bir örneğini izin veren bir statik olmayan sınıf oluşturmak için bkz [C# uygulama Singleton](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316%28v=pandp.10%29).  
  
 Aşağıdaki listede, bir statik sınıf'larının temel özellikleri sağlar:  
  
- Yalnızca statik üyeleri içerir.  
  
- Örneği oluşturulamıyor.  
  
- Korumalı.  
  
- İçeremez [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Statik bir sınıf oluşturma bu nedenle temel olarak, yalnızca statik üyeleri ve özel bir oluşturucu içeren bir sınıf oluşturma aynıdır. Özel bir oluşturucu, sınıfı oluşturulmasını engeller. Statik bir sınıfı kullanmanın avantajı, derleyici, hiçbir örnek üyeleri yanlışlıkla eklendiğinden emin olmak için kontrol edebilirsiniz olmasıdır. Derleyici, bu sınıfın örneklerinin oluşturulup garanti eder.  
  
 Statik sınıflar mühürlendi ve bu nedenle devralınamaz. Dışında herhangi bir sınıftan devralamaz <xref:System.Object>. Statik sınıflar, bir örnek oluşturucusunda içeremez; Ancak, bir statik Oluşturucu içerebilirler. Önemsiz başlatma gerektiren statik üyeler sınıf içeriyorsa, statik olmayan sınıf statik Oluşturucu da tanımlamanız gerekir. Daha fazla bilgi için [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="example"></a>Örnek  
 Sıcaklık Fahrenhayt için Santigrat ve Fahrenhayt derece için dönüştürme iki yöntem içeren bir statik sınıfın bir örnek aşağıda verilmiştir:  
  
 [!code-csharp[csProgGuideObjects#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#31)]  
  
## <a name="static-members"></a>Statik Üyeler  
 Statik olmayan sınıf statik yöntemler, alanlar, özellikler veya olaylar içerebilir. Hatta sınıfının hiçbir örneği oluşturulduğunda statik üye sınıfta çağrılabilir. Statik üye sınıfı adı, örnek adını her zaman erişilebilir. Statik bir üyenin yalnızca bir kopyasını mevcut sınıfının kaç tane bağımsız olarak oluşturulur. Statik yöntemler ve Özellikler statik olmayan alanlar ve olaylar, içeren türlerine erişemez ve açıkça bir yöntem parametresi geçirilir sürece herhangi bir nesnenin bir örnek değişkeni erişemez.  
  
 Sınıfın tamamı statik olarak bildirmek daha bazı statik üyesi olan bir statik olmayan sınıf bildirmek için daha tipik bir durumdur. Statik alan iki genel kullanım örneği nesnelerin sayısını tutmak veya tüm örnekleri arasında paylaşılan bir değeri depolamak için verilebilir.  
  
 Statik yöntemler aşırı ancak sınıfına değil de herhangi bir sınıfın örneğini ait olduğundan, geçersiz kılınan değil.  
  
 Bir alan olarak bildirilemez rağmen `static const`, [const](../../../csharp/language-reference/keywords/const.md) temelde, davranışı statik alan. Tür örnekleri için bir türe ait. Bu nedenle, const alanları aynı kullanarak erişilebilir `ClassName.MemberName` statik alanlar için kullanılan bir gösterimi. Hiçbir nesne örneği gereklidir.  
  
 C# statik yerel değişkenler (yöntemi kapsamda bildirilen değişkenler) desteklemez.  
  
 Kullanarak statik sınıf üyeleri bildirme `static` anahtar sözcüğü aşağıdaki örnekte gösterildiği gibi üyenin dönüş türünden önce:  
  
 [!code-csharp[csProgGuideObjects#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#29)]  
  
 Statik üyeleri, statik üye ilk kez ve daha önce statik oluşturucuyu erişmeden önce başlatılır varsa, çağrılır. Bir statik sınıf üyesine erişmek için sınıfın adını bir değişken adı yerine üye konumunu belirtmek için aşağıdaki örnekte gösterildiği gibi kullanın:  
  
 [!code-csharp[csProgGuideObjects#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#30)]  
  
 Sınıfınıza statik alanlar içeriyorsa, sınıf yüklendiğinde, bunları başlatır ve statik bir oluşturucu sağlayın.  
  
 Bir örnek yöntemine bir çağrı davranırken statik bir yöntem çağrısı bir çağrı talimatı Microsoft Ara dilini (MSIL) oluşturur. bir `callvirt` null bir nesneye başvuruda için ve ayrıca denetleyen yönergesi. Ancak, çoğu zaman ikisi arasındaki performans farkı önemli değildir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [statik sınıflar](~/_csharplang/spec/classes.md#static-classes) ve [statik ve örnek üyeleri](~/_csharplang/spec/classes.md#static-and-instance-members) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [static](../../../csharp/language-reference/keywords/static.md)
- [Sınıflar](../../../csharp/programming-guide/classes-and-structs/classes.md)
- [class](../../../csharp/language-reference/keywords/class.md)
- [Statik Oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)
- [Örnek Oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)
