---
title: Erişim Değiştiricileri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: ec275d4782fee047b16fd114c4d22ceb03eecb11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="access-modifiers-c-programming-guide"></a>Erişim Değiştiricileri (C# Programlama Kılavuzu)
Tüm türleri ve tür üyeleri derlemenizi veya diğer derlemelerden diğer koddan kullanılabilmesi için olup olmadığını denetleyen bir erişilebilirlik düzeyi vardır. Aşağıdaki erişim değiştiricileri bildirirken ne zaman bir tür veya üye erişilebilirliğini belirtmek için kullanabilirsiniz:  
  
 [public](../../../csharp/language-reference/keywords/public.md)  
 Tür veya üye, başka bir kod aynı bütünleştirilmiş kodda ya da başvurduğu başka bir derleme tarafından erişilebilir. 
  
 [private](../../../csharp/language-reference/keywords/private.md)  
 Tür veya üye, yalnızca aynı sınıfta veya yapı kodda tarafından erişilebilir.  
  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 Tür veya üye yalnızca kodu aynı sınıfın veya bu sınıftan türetilmiş bir sınıf tarafından erişilebilir.  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 Tür veya üye, herhangi bir kod aynı bütünleştirilmiş kodda değiştirebilir, ancak başka bir derleme tarafından erişilebilir.  
  
 [İç korumalı](../../../csharp/language-reference/keywords/protected-internal.md) tür veya üye, bildirildiği veya içinden bütünleştirilmiş kod tarafından erişilebilecek başka bir derleme türetilen bir sınıfta. 

 [korumalı özel](../../../csharp/language-reference/keywords/private-protected.md) tür veya üye bildiren derlemede yalnızca kendi kodu aynı sınıfın veya bu sınıftan türetilen bir tür erişebilir.
  
 Aşağıdaki örnekler bir tür ve üye erişim değiştiricileri belirtme göstermektedir:  
  
 [!code-csharp[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]  
  
 Tüm erişim değiştiricileri tüm türleri veya tüm bağlamlarında üyeleri tarafından kullanılabilir ve bazı durumlarda bir tür üyesi erişilebilirliğini içeren türünü erişilebilirlik tarafından sınırlı değildir. Aşağıdaki bölümler erişilebilirlik hakkında daha fazla ayrıntı sağlar.  
  
## <a name="class-and-struct-accessibility"></a>Sınıf ve yapı erişilebilirlik  
 Sınıflar ve doğrudan bir ad alanı (diğer sınıf veya yapı içinde yuvalanmış olmayan diğer sözcükler,) içinde bildirilen yapılar ortak ya da iç olabilir. Herhangi bir erişim değiştiricisi belirtilmezse varsayılan iç kullanılır.  
  
 İç içe geçmiş sınıflar ve yapılar, gibi yapı üyeleri olarak genel, iç veya özel bildirilebilir. Sınıf üyeleri, iç içe geçmiş sınıflar ve yapılar dahil olmak üzere, ortak olabilir, korumalı iç, korumalı, dahili, özel korumalı veya özel. Sınıf üyeleri ve iç içe geçmiş sınıflar ve yapılar, gibi yapı üyeleri için erişim düzeyi varsayılan olarak özeldir. Özel iç içe geçmiş türler içeren tür dışında erişilebilir değildir.  
  
 Türetilmiş sınıflar temel türlerini daha büyük erişilebilirlik sahip olamaz. Diğer bir deyişle, ortak bir sınıf olamaz `B` bir iç sınıfın türeyen `A`. Bu izin, yapma etkisini olurdu `A` ortak, çünkü tüm korumalı veya iç üyeleri `A` türetilmiş sınıftan erişilebilir.  
  
 Belirli etkinleştirebilirsiniz, iç türlerinizi Internalsvisibletoattribute kullanarak erişmek için diğer derlemeler. Daha fazla bilgi için bkz: [arkadaş derlemeleri](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
## <a name="class-and-struct-member-accessibility"></a>Sınıf ve yapı üyesi erişilebilirlik  
 Sınıf üyeleri (iç içe geçmiş sınıflar ve yapılar dahil) erişim altı tür ile bildirilebilir. Yapı üyeleri yapılar devralma desteklemediği için korumalı olarak bildirilemez.  
  
 Normalde, bir üye erişilebilirliğini içerdiği türü erişilebilirlik büyük değil. Ancak, üye arabirim yöntemleri uygulayan veya ortak bir taban sınıf içinde tanımlı sanal yöntemlerini geçersiz kılar, genel bir iç sınıf üyesi derleme dışında erişilebilir olabilir.  
  
 Tür alanı, özelliği veya olay herhangi bir üyenin en az üye olarak olarak erişilebilir olmalıdır. Benzer şekilde, dönüş türü ve parametre türleri bir yöntemi, dizin oluşturucu veya temsilci herhangi bir üyenin en az üye olarak olarak erişilebilir olmalıdır. Örneğin, ortak bir yöntem olamaz `M` bir sınıf döndüren `C` sürece `C` de geneldir. Benzer şekilde, korumalı bir özellik türü olamaz `A` varsa `A` özel olarak bildirilmedi.  
  
 Kullanıcı tanımlı işleçler her zaman ortak olarak bildirilmelidir. Daha fazla bilgi için bkz: [işleci (C# Başvurusu)](../../../csharp/language-reference/keywords/operator.md).  
  
 Sonlandırıcılar erişilebilirlik değiştiricileri sahip olamaz.  
  
 Bir sınıf veya yapı üyesi için erişim düzeyi ayarlamak için aşağıdaki örnekte gösterildiği gibi üye bildirimi için uygun anahtar sözcüğünü ekleyin.  
  
 [!code-csharp[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]  
  
> [!NOTE]
>  Korumalı iç erişilebilirlik düzeyi korumalı veya dahili, not anlamına gelmektedir korumalı ve iç. Diğer bir deyişle, korumalı bir iç üye türetilen sınıflar dahil olmak üzere aynı bütünleştirilmiş kodda, herhangi bir sınıftan erişilebilir. Yalnızca türetilmiş sınıflar aynı bütünleştirilmiş kodda erişilebilirlik sınırlamak için sınıf iç bildirme ve üyeleri korumalı olarak bildirin. Ayrıca, C# 7.2 ile başlayarak, özel korumalı erişim değiştiricisi içeren sınıf iç yapmaya gerek kalmadan aynı sonucu elde etmek için kullanabilirsiniz.  
  
## <a name="other-types"></a>Diğer türleri  
 Bildirilen arabirimleri gibi ortak veya dahili bir ad alanı içinde doğrudan bildirilebilir ve sınıflar ve yapılar, arabirimleri varsayılan iç erişmek için olduğu gibi. Arabirim üyeleri her zaman bir sınıf veya yapı erişmek diğer türleri etkinleştirmek için bir arabirim amacı olduğu için ortaktır. Erişim değiştiricileri arabirimi üyelerine uygulanabilir.  
  
 Numaralandırma üyeleri her zaman ortak ve hiçbir erişim değiştiricileri uygulanabilir.  
  
 Temsilciler sınıflar ve yapılar gibi davranır. Varsayılan olarak, bunlar doğrudan ad alanı içinde bildirirken iç erişim ve iç içe geçmiş olduğunda özel erişimi var.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [protected internal](../../../csharp/language-reference/keywords/protected-internal.md)  
 [private protected](../../../csharp/language-reference/keywords/private-protected.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [interface](../../../csharp/language-reference/keywords/interface.md)
