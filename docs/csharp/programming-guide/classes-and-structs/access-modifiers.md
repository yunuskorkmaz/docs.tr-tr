---
title: Erişim Değiştiricileri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 6be0ae4f6497dfb2db9607f61c4ede5083d57dc7
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271357"
---
# <a name="access-modifiers-c-programming-guide"></a>Erişim Değiştiricileri (C# Programlama Kılavuzu)
Tüm türler ve tür üyeleri, derlemenizin veya diğer derlemelere başka koddan kullanılıp kullanılamayacağını denetleyen bir erişilebilirlik düzeyi vardır. Aşağıdaki erişim değiştiriciler, tür veya üyenin erişilebilirliğini bildirirken zaman belirtmek için kullanabilirsiniz:  
  
 [public](../../../csharp/language-reference/keywords/public.md)  
 Türe veya üyeye aynı derlemenin veya ona başvuran başka bir derleme içindeki diğer kodlardan tarafından erişilebilir. 
  
 [private](../../../csharp/language-reference/keywords/private.md)  
 Tür veya üye, yalnızca aynı sınıf veya yapı içindeki kod tarafından erişilebilir.  
  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 Türe veya üyeye aynı sınıftaki veya bu sınıftan türetilen bir sınıfta kod yalnızca tarafından erişilebilir.  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 Türe veya üyeye aynı derlemedeki ancak farklı derlemeyle herhangi bir kod tarafından erişilebilir.  
  
 [İç korumalı](../../../csharp/language-reference/keywords/protected-internal.md) türe veya üyeye bildirildiği içinden veya derlemedeki kod ile erişilebilir başka bir derlemedeki türetilmiş bir sınıf. 

 [Özel korumalı](../../../csharp/language-reference/keywords/private-protected.md) kodu aynı sınıftaki veya bu sınıftan türetilmiş bir tür tarafından türün veya üyenin yalnızca bildirme derlemesi, erişilebilir.
  
 Aşağıdaki örnekler, bir tür ve üye erişim değiştiricileri belirtmeniz göstermektedir:  
  
 [!code-csharp[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]  
  
 Tüm erişim değiştiricileri tüm türleri veya üyeleri tüm bağlamlarda tarafından kullanılabilir ve bazı durumlarda bir tür üyesi erişilebilirliği kapsayan türü erişilebilirliğini tarafından sınırlanır. Aşağıdaki bölümler, erişilebilirlik hakkında daha fazla ayrıntı sağlar.  
  
## <a name="class-and-struct-accessibility"></a>Sınıf ve yapı erişilebilirlik  
 Sınıfları ve doğrudan bir ad alanı (diğer sınıflar veya yapılar içinde yuvalanmış değil, başka bir deyişle,) içinde bildirilen yapıları, public veya internal olabilir. Hiçbir erişim değiştiricisi belirtilmişse iç varsayılandır.  
  
 İç içe geçmiş sınıflar ve yapılar, dahil olmak üzere, Yapı üyeleri olarak genel, iç veya özel olarak bildirilebilir. Sınıf üyeleri, iç içe geçmiş sınıflar ve yapılar dahil olmak üzere, genel, korumalı iç, korumalı, dahili, özel korumalı veya özel. Sınıf üyeleri ve iç içe geçmiş sınıflar ve yapılar, dahil olmak üzere, Yapı üyeleri için erişim düzeyi varsayılan olarak özeldir. Özel iç içe geçmiş türler içeren tür dışında erişilebilir değildir.  
  
 Türetilmiş sınıflar temel türleri değerinden daha büyük düzeyde erişilebilirlik sahip olamaz. Diğer bir deyişle, bir ortak sınıf olamaz `B` iç bir sınıftan türetilen `A`. Bu izin verilirse, bu duruma getirme yarayıp `A` genel, çünkü tüm korumalı veya iç üyeleri `A` türetilmiş sınıftan erişilebilir.  
  
 Belirli etkinleştirmek ınternalsvisibletoattribute özniteliğini kullanarak tarafından iç türlerine erişmek için diğer derlemeler. Daha fazla bilgi için [arkadaş derlemeleri](../concepts/assemblies-gac/friend-assemblies.md).  
  
## <a name="class-and-struct-member-accessibility"></a>Sınıf ve yapı üyesi erişilebilirliği  
 Sınıf üyeleri (iç içe geçmiş sınıflar ve yapılar dahil) erişim altı tür ile bildirilebilir. Yapı üyeleri, yapılar devralımı desteklemez çünkü korumalı olarak bildirilemez.  
  
 Normalde, bir üyenin erişilebilirliğini içeren türün erişilebilirlik büyük değil. Ancak, genel bir iç sınıf üyesi üye arabirim yöntemleri uygulayan ya da genel bir temel sınıfta tanımlanan sanal yöntemleri geçersiz kılan derlemenin dışından erişilebilir olabilir.  
  
 Bir alan, özellik veya olay herhangi bir üyenin türü en az üyesi olarak olarak erişilebilir olması gerekir. Benzer şekilde, dönüş türü ve parametre türleri, yöntem, dizin oluşturucu veya temsilci olan herhangi bir üyenin en az üyesi olarak olarak erişilebilir olmalıdır. Örneğin, bir genel yöntem olamaz `M` bir sınıf döndüren `C` sürece `C` ayrıca geneldir. Benzer şekilde, bir korumalı özellik türü olamaz `A` varsa `A` özel olarak bildirilir.  
  
 Kullanıcı tanımlı işleçler her zaman ortak olarak bildirilmelidir. Daha fazla bilgi için [işleci (C# Başvurusu)](../../../csharp/language-reference/keywords/operator.md).  
  
 Sonlandırıcılar erişilebilirlik değiştiricileri olamaz.  
  
 Uygun anahtar sözcüğü bir sınıf veya yapı üyesi için erişim düzeyi ayarlamak için üye bildirimi için aşağıdaki örnekte gösterildiği gibi ekleyin.  
  
 [!code-csharp[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]  
  
> [!NOTE]
>  Korumalı dahili erişilebilirlik düzeyi korumalı veya iç, not anlamına gelir. korumalı ve iç. Diğer bir deyişle, korumalı, dahili bir üye aynı derlemedeki türetilmiş sınıflar da dahil olmak üzere herhangi bir sınıftan erişilebilir. Aynı derlemenin yalnızca türetilmiş sınıflarda erişilebilirlik sınırlamak için sınıfı iç bildirmek ve üyeleri protected olarak bildirin. Ayrıca, C# 7.2 ile başlayarak, kapsayan sınıfı iç yapmaya gerek kalmadan aynı sonucu elde etmek için özel bir korumalı erişim değiştiricisi kullanabilirsiniz.  
  
## <a name="other-types"></a>Diğer türleri  
 Bildirilen arabirimleri, ortak veya iç olarak ad alanı içinde doğrudan bildirilebilir ve sınıflar ve yapılar, arabirimler varsayılan iç erişimi olduğu gibi. Arabirim üyeleri, her zaman bir sınıf veya yapı erişmek diğer türleri etkinleştirmek için bir arabirim amacı olduğu için ortaktır. Hiçbir erişim değiştiricisine arabirimi üyelerine uygulanabilir.  
  
 Her zaman numaralandırma üyelerini genel ve hiçbir erişim değiştiricisine uygulanabilir.  
  
 Temsilciler, sınıflar ve yapılar gibi davranır. Varsayılan olarak, doğrudan ad alanı içinde bildirildiğinde iç erişim ve iç içe olduğunda özel erişime sahiptirler.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [public](../../../csharp/language-reference/keywords/public.md)  
- [internal](../../../csharp/language-reference/keywords/internal.md)  
- [protected](../../../csharp/language-reference/keywords/protected.md)  
- [protected internal](../../../csharp/language-reference/keywords/protected-internal.md)  
- [private protected](../../../csharp/language-reference/keywords/private-protected.md)  
- [class](../../../csharp/language-reference/keywords/class.md)  
- [struct](../../../csharp/language-reference/keywords/struct.md)  
- [interface](../../../csharp/language-reference/keywords/interface.md)
