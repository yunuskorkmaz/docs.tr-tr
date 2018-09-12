---
title: Statik Sınıflar ve Statik Sınıf Üyeleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 60a75946d30b1555aea01507d846e790dd00f767
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44509674"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Statik Sınıflar ve Statik Sınıf Üyeleri (C# Programlama Kılavuzu)
A [statik](../../../csharp/language-reference/keywords/static.md) sınıfı, temel bir statik olmayan sınıf ile aynı, ancak bir fark vardır: bir statik sınıfın örneği oluşturulamıyor. Diğer bir deyişle, kullanamazsınız [yeni](../../../csharp/language-reference/keywords/new.md) sınıf türünde bir değişken oluşturmak için anahtar sözcüğü. Hiçbir örnek değişken olduğundan, bir statik sınıf üyeleri sınıf adı'ı kullanarak erişir. Örneğin, bir statik sınıflar varsa adlı `UtilityClass` adlı bir genel yöntem olan `MethodA`, aşağıdaki örnekte gösterildiği gibi yöntemi çağırın:  
  
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
  
 Tüm sınıf türleri ile olduğu gibi bir statik sınıf için tür bilgileri tarafından yüklenir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ortak dil çalışma zamanı (CLR) sınıfı başvuran program yüklendiğinde. Program, tam olarak ne zaman sınıfı yüklenen belirtemezsiniz. Ancak, yüklenecek ve başlatılmış kendi alanlarına ve sınıf programınızı ilk kez başvuruluyor önce çağırılır, statik Oluşturucu sağlanır. Statik Oluşturucu yalnızca bir kez çağrılır ve statik sınıf programınızı bulunduğu uygulama etki alanı ömrü boyunca bellekte kalır.  
  
> [!NOTE]
>  Oluşturulacak kendisi yalnızca bir örneğini izin veren bir statik olmayan sınıf oluşturmak için bkz [C# uygulama Singleton](https://msdn.microsoft.com/library/ms998558.aspx).  
  
 Aşağıdaki listede, bir statik sınıf'larının temel özellikleri sağlar:  
  
-   Yalnızca statik üyeleri içerir.  
  
-   Örneği oluşturulamıyor.  
  
-   Korumalı.  
  
-   İçeremez [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Statik bir sınıf oluşturma bu nedenle temel olarak, yalnızca statik üyeleri ve özel bir oluşturucu içeren bir sınıf oluşturma aynıdır. Özel bir oluşturucu, sınıfı oluşturulmasını engeller. Statik bir sınıfı kullanmanın avantajı, derleyici, hiçbir örnek üyeleri yanlışlıkla eklendiğinden emin olmak için kontrol edebilirsiniz olmasıdır. Derleyici, bu sınıfın örneklerinin oluşturulup garanti eder.  
  
 Statik sınıflar mühürlendi ve bu nedenle devralınamaz. Dışında herhangi bir sınıftan devralamaz <xref:System.Object>. Statik sınıflar, bir örnek oluşturucusunda içeremez; Ancak, bir statik Oluşturucu içerebilirler. Önemsiz başlatma gerektiren statik üyeler sınıf içeriyorsa, statik olmayan sınıf statik Oluşturucu da tanımlamanız gerekir. Daha fazla bilgi için [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="example"></a>Örnek  
 Sıcaklık Fahrenhayt için Santigrat ve Fahrenhayt derece için dönüştürme iki yöntem içeren bir statik sınıfın bir örnek aşağıda verilmiştir:  
  
 [!code-csharp[csProgGuideObjects#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_1.cs)]  
  
## <a name="static-members"></a>Statik Üyeler  
 Statik olmayan sınıf statik yöntemler, alanlar, özellikler veya olaylar içerebilir. Hatta sınıfının hiçbir örneği oluşturulduğunda statik üye sınıfta çağrılabilir. Statik üye sınıfı adı, örnek adını her zaman erişilebilir. Statik bir üyenin yalnızca bir kopyasını mevcut sınıfının kaç tane bağımsız olarak oluşturulur. Statik yöntemler ve Özellikler statik olmayan alanlar ve olaylar, içeren türlerine erişemez ve açıkça bir yöntem parametresi geçirilir sürece herhangi bir nesnenin bir örnek değişkeni erişemez.  
  
 Sınıfın tamamı statik olarak bildirmek daha bazı statik üyesi olan bir statik olmayan sınıf bildirmek için daha tipik bir durumdur. Statik alan iki genel kullanım örneği nesnelerin sayısını tutmak veya tüm örnekleri arasında paylaşılan bir değeri depolamak için verilebilir.  
  
 Statik yöntemler aşırı ancak sınıfına değil de herhangi bir sınıfın örneğini ait olduğundan, geçersiz kılınan değil.  
  
 Bir alan olarak bildirilemez rağmen `static const`, [const](../../../csharp/language-reference/keywords/const.md) temelde, davranışı statik alan. Tür örnekleri için bir türe ait. Bu nedenle, const alanları aynı kullanarak erişilebilir `ClassName.MemberName` statik alanlar için kullanılan bir gösterimi. Hiçbir nesne örneği gereklidir.  
  
 C# statik yerel değişkenler (yöntemi kapsamda bildirilen değişkenler) desteklemez.  
  
 Kullanarak statik sınıf üyeleri bildirme `static` anahtar sözcüğü aşağıdaki örnekte gösterildiği gibi üyenin dönüş türünden önce:  
  
 [!code-csharp[csProgGuideObjects#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_2.cs)]  
  
 Statik üyeleri, statik üye ilk kez ve daha önce statik oluşturucuyu erişmeden önce başlatılır varsa, çağrılır. Bir statik sınıf üyesine erişmek için sınıfın adını bir değişken adı yerine üye konumunu belirtmek için aşağıdaki örnekte gösterildiği gibi kullanın:  
  
 [!code-csharp[csProgGuideObjects#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_3.cs)]  
  
 Sınıfınıza statik alanlar içeriyorsa, sınıf yüklendiğinde, bunları başlatır ve statik bir oluşturucu sağlayın.  
  
 Bir örnek yöntemine bir çağrı davranırken statik bir yöntem çağrısı bir çağrı talimatı Microsoft Ara dilini (MSIL) oluşturur. bir `callvirt` null bir nesneye başvuruda için ve ayrıca denetleyen yönergesi. Ancak, çoğu zaman ikisi arasındaki performans farkı önemli değildir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [static](../../../csharp/language-reference/keywords/static.md)  
- [Sınıflar](../../../csharp/programming-guide/classes-and-structs/classes.md)  
- [class](../../../csharp/language-reference/keywords/class.md)  
- [Statik Oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
- [Örnek Oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)
