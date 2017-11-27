---
title: "Statik Sınıflar ve Statik Sınıf Üyeleri (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
caps.latest.revision: "49"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cf2517dd5989d36341b840ffcb476cbeb14baf54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Statik Sınıflar ve Statik Sınıf Üyeleri (C# Programlama Kılavuzu)
A [statik](../../../csharp/language-reference/keywords/static.md) sınıfı, aslında bir statik olmayan sınıf ile aynı, ancak bir fark yoktur: statik sınıf örneği oluşturulamıyor. Diğer bir deyişle, kullanamazsınız [yeni](../../../csharp/language-reference/keywords/new.md) sınıfı türünde bir değişken oluşturmak için anahtar sözcüğü. Hiçbir örnek değişken olduğundan, statik sınıf üyeleri sınıf adı kullanarak erişir. Örneğin, bu sınıfı statik varsa adlı `UtilityClass` adlı ortak bir yöntemi olan `MethodA`, aşağıdaki örnekte gösterildiği gibi yöntemini çağırın:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Statik sınıf yalnızca giriş parametrelerine çalışan ve get veya tüm iç örneği alanları gerekmez yöntemleri kümeleri için uygun bir kapsayıcı olarak kullanılabilir. Örneğin, .NET Framework Sınıf Kitaplığı'nda, statik <xref:System.Math?displayProperty=nameWithType> sınıfı içeren depolama veya belirli bir örneği için benzersiz olan veri almak için herhangi bir gereksinim olmadan matematik işlemlerini gerçekleştiren yöntemleri <xref:System.Math> sınıfı. Diğer bir deyişle, sınıf üyeleri sınıfı adı ve yöntem adını belirterek aşağıdaki örnekte gösterildiği gibi uygulayın.  
  
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
  
 Tüm sınıf türleri ile olduğu gibi statik sınıf için tür bilgisi tarafından yüklenen [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ortak dil çalışma zamanı (CLR) sınıfı başvuran program yüklendiğinde. Program, tam olarak ne zaman sınıfı yüklenen belirtemezsiniz. Ancak, yüklenmesi ve başlatılan alanlarını ve sınıf programınızdaki ilk kez başvuruluyor önce çağırılır, statik Oluşturucusu sağlanır. Statik Oluşturucu yalnızca bir kez çağrılır ve statik sınıf programınızı bulunduğu uygulama etki alanı için kullanım ömrünü bellekte kalır.  
  
> [!NOTE]
>  Kendisini oluşturulması için yalnızca bir örneğine izin veren bir statik olmayan sınıf oluşturmak için bkz: [uygulama Singleton C#](http://go.microsoft.com/fwlink/?LinkID=100567).  
  
 Aşağıdaki listede statik sınıf ana özelliklerini sağlar:  
  
-   Yalnızca statik üyeler içeriyor.  
  
-   Örneği oluşturulamıyor.  
  
-   Korumalı değil.  
  
-   İçeremez [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Bir statik sınıf oluşturma bu nedenle temelde yalnızca statik üyeleri ve bir özel oluşturucu içeren bir sınıf oluşturma ile aynıdır. Özel oluşturucu sınıfı oluşturulmasını engeller. Statik sınıf kullanmanın avantajı, derleyici hiçbir örnek üyesinin yanlışlıkla eklendiğinden emin olmak için kontrol edebilirsiniz ' dir. Derleyici, bu sınıfın örnekleri, oluşturulamıyor garanti.  
  
 Statik sınıflar mühürlendi ve bu nedenle devralındı. Dışında herhangi bir sınıftan devralınan olamaz <xref:System.Object>. Statik sınıflar örnek oluşturucu içeremez; Bununla birlikte, bunlar statik Oluşturucu içerebilir. Sınıf Önemsiz olmayan başlatma gerektiren statik üyeler içeriyorsa, statik olmayan sınıfları ayrıca statik Oluşturucu tanımlamanız gerekir. Daha fazla bilgi için bkz: [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="example"></a>Örnek  
 Burada, fahrenhayt derece ve derece Fahrenhayt sıcaklık Dönüştür iki yöntemleri içeren bir statik sınıf örneği verilmiştir:  
  
 [!code-csharp[csProgGuideObjects#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_1.cs)]  
  
## <a name="static-members"></a>Statik Üyeler  
 Statik olmayan sınıfı statik yöntemler, alanları, özellikleri veya olayları içerebilir. Statik üye bile sınıfının hiçbir örneği oluşturulduğunda bir sınıf üzerinde çağrılabilir. Statik üye sınıfı adı, örnek adı her zaman erişilir. Kaç tane sınıfın örnekleri, oluşturulan bağımsız olarak yalnızca bir kopyasını statik bir üyenin bulunmaktadır. Statik yöntemler ve Özellikler statik olmayan alanlar ve kendilerini kapsayan türle olayları erişemez ve açıkça bir yöntem parametresinde geçirilen sürece herhangi bir nesnenin bir örnek değişkeni erişemiyor.  
  
 Statik olarak sınıfının tümüne bildirmek üzere daha bazı statik üyeleri olan bir statik olmayan sınıfı bildirmek için daha genel bir durumdur. Statik alanları iki yaygın kullanımları şunlardır: örneği nesneleri sayısını tutmak için ya da tüm örnekler arasında paylaşılan bir değeri depolamak için.  
  
 Statik yöntemler aşırı ancak sınıfı ve değil sınıfın örneklerini ait olduğundan, geçersiz.  
  
 Bir alan olarak bildirilemez rağmen `static const`, [const](../../../csharp/language-reference/keywords/const.md) alandır davranışını içinde temelde statik. Türünün örnekleri için türüne ait. Bu nedenle, const alanları aynı kullanarak erişilebilir `ClassName.MemberName` statik alanlar için kullanılan gösterimi. Hiçbir nesne örneği gereklidir.  
  
 C# statik yerel değişkenler (yöntemi kapsamda bildirilen değişkenler) desteklemez.  
  
 Kullanarak statik sınıf üyeleri bildirme `static` anahtar sözcüğü dönüş türü üyesinin aşağıdaki örnekte gösterildiği gibi önce:  
  
 [!code-csharp[csProgGuideObjects#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_2.cs)]  
  
 Statik üyeler statik üyenin ilk kez ve statik Oluşturucusu önce erişmeden önce başlatılır varsa, adı verilir. Statik sınıf üyesine erişme için sınıfı adı değişken adı yerine üye konumunu belirtmek için aşağıdaki örnekte gösterildiği gibi kullanın:  
  
 [!code-csharp[csProgGuideObjects#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_3.cs)]  
  
 Sınıfınızda statik alanları içeriyorsa, sınıf yüklendiğinde, bunları başlatır statik Oluşturucu sağlayın.  
  
 Bir örnek yöntemine yapılan bir çağrı davranırken bir statik yöntem çağrısı bir çağrı yönergesi Microsoft Ara dili (MSIL) oluşturur. bir `callvirt` null bir nesne başvuran için ve ayrıca denetleyen yönerge. Bununla birlikte, çoğu zaman iki arasındaki performans farkının önemli değildir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [statik](../../../csharp/language-reference/keywords/static.md)  
 [Sınıfları](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [sınıfı](../../../csharp/language-reference/keywords/class.md)  
 [Statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
 [Örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)
