---
title: Erişim değiştiricileri- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 0d8e536902317c1e5b00dadde069dd6242189088
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705671"
---
# <a name="access-modifiers-c-programming-guide"></a>Erişim Değiştiricileri (C# Programlama Kılavuzu)
Tüm türler ve tür üyeleri, derlemenizin veya diğer derlemelerinizdeki diğer koddan kullanılıp kullanılamayacağını denetleyen bir erişilebilirlik düzeyine sahiptir. Aşağıdaki erişim değiştiricilerini, bir tür veya üyenin bildirimini yaparken belirtmek için kullanabilirsiniz:  
  
 [public](../../language-reference/keywords/public.md)  
 Türe veya üyeye aynı derlemedeki veya buna başvuran başka bir derlemede bir veya daha fazla kod tarafından erişilebilir. 
  
 [private](../../language-reference/keywords/private.md)  
 Türe veya üyeye yalnızca aynı sınıf veya yapı içindeki kodla erişilebilir.  
  
 [protected](../../language-reference/keywords/protected.md)  
 Türe veya üyeye yalnızca aynı sınıftaki kodla veya bu sınıftan türetilmiş bir sınıfta erişilebilir.  
 [internal](../../language-reference/keywords/internal.md)  
 Türe veya üyeye aynı derlemedeki kod tarafından erişilebilir, ancak başka bir derlemeden erişilebilir.  
  
 [korumalı iç](../../language-reference/keywords/protected-internal.md) Türe veya üyeye, bildirildiği derlemede ya da başka bir derlemedeki türetilmiş bir sınıftan erişilebilen herhangi bir kod tarafından erişilebilir. 

 [özel korumalı](../../language-reference/keywords/private-protected.md) Türe veya üyeye yalnızca bildirim derlemesi içinde, aynı sınıftaki veya bu sınıftan türetilmiş bir türde koda erişilebilir.
  
 Aşağıdaki örneklerde, bir tür ve üye üzerinde erişim değiştiricilerin nasıl belirtildiğini gösterilmektedir:  
  
 [!code-csharp[csProgGuideObjects#72](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#72)]  
  
 Tüm erişim değiştiricileri tüm bağlamlardaki tüm türler veya Üyeler tarafından kullanılamaz ve bazı durumlarda bir tür üyesinin erişilebilirliği, kapsayan türünün erişilebilirliği tarafından kısıtlanıyor. Aşağıdaki bölümler erişilebilirlik hakkında daha fazla ayrıntı sağlar.  
  
## <a name="class-and-struct-accessibility"></a>Sınıf ve yapı erişilebilirliği  
 Bir ad alanı içinde doğrudan tanımlanmış sınıflar ve yapılar (diğer bir deyişle, diğer sınıfların veya yapıların içinde iç içe olmayan), genel veya iç olabilir. Bir erişim değiştiricisi belirtilmemişse, iç varsayılandır.  
  
 İç içe sınıflar ve yapılar dahil yapı üyeleri, genel, iç veya özel olarak bildirilebilecek. İç içe sınıflar ve yapılar dahil olmak üzere sınıf üyeleri ortak, korumalı dahili, korunan, dahili, özel korumalı veya özel olabilir. Sınıf üyeleri ve yapı üyeleri için iç içe sınıflar ve yapılar dahil erişim düzeyi varsayılan olarak özeldir. Özel iç içe türlere, kapsayan türün dışından erişilemez.  
  
 Türetilmiş sınıfların temel türlerinden daha fazla erişilebilirliği olamaz. Diğer bir deyişle, bir iç sınıftan türetilen `B` ortak bir sınıfa sahip olamaz `A`. Buna izin veriliyorsa, tüm `A` korunan veya iç üyelerine türetilmiş sınıftan erişilebilir olduğundan `A` genel hale getirme etkisi vardır.  
  
 InternalsVisibleToAttribute kullanarak, özel diğer derlemelerin iç türlerinizi erişmesini sağlayabilirsiniz. Daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).  
  
## <a name="class-and-struct-member-accessibility"></a>Sınıf ve yapı üye erişilebilirliği  
 Sınıf üyeleri (iç içe geçmiş sınıflar ve yapılar dahil) altı erişim türlerinden herhangi biriyle bildirilebilecek. Yapılar devralmayı desteklemediğinden, yapı üyeleri korumalı olarak bildirilemez.  
  
 Normalde, bir üyenin erişilebilirliği onu içeren türün erişilebilirliğiyle daha büyük değildir. Ancak, üye arabirim yöntemleri uygularsa veya ortak bir temel sınıfta tanımlanan sanal yöntemleri geçersiz kıldığında, iç sınıfın ortak bir üyesine derleme dışından erişilebilir.  
  
 Bir alan, özellik veya olay olan herhangi bir üyenin türü, en azından üyenin kendisi olarak erişilebilir olmalıdır. Benzer şekilde, dönüş türü ve bir yöntem, Dizin Oluşturucu ya da temsilci olan herhangi bir üyenin parametre türleri en azından üyenin kendisi olarak erişilebilir olmalıdır. Örneğin, `C` da genel olmadığı müddetçe bir sınıf `C` döndüren `M` ortak bir metoda sahip olabilirsiniz. Benzer şekilde, `A` Private olarak bildirilirse `A` türünde korumalı bir özelliği olamaz.  
  
 Kullanıcı tanımlı işleçler her zaman ortak ve statik olarak bildirilmelidir. Daha fazla bilgi için bkz. [operatör aşırı yüklemesi](../../language-reference/operators/operator-overloading.md).  
  
 Sonlandırıcılar erişilebilirlik değiştiricilerine sahip olamaz.  
  
 Bir sınıf veya yapı üyesinin erişim düzeyini ayarlamak için, aşağıdaki örnekte gösterildiği gibi, üye bildirimine uygun anahtar sözcüğü ekleyin.  
  
 [!code-csharp[csProgGuideObjects#73](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#73)]  
  
> [!NOTE]
> Korunan iç erişilebilirlik düzeyi korumalı veya dahili, korumalı ve dahili anlamına gelir. Diğer bir deyişle, korunan bir iç üyeye, türetilmiş sınıflar dahil olmak üzere aynı derlemedeki herhangi bir sınıftan erişilebilir. Erişilebilirliği yalnızca aynı derlemede bulunan türetilmiş sınıflarla sınırlamak için, sınıfın kendisini iç bildirin ve üyelerini korumalı olarak bildirin. Ayrıca, 7,2 ile C# başlayarak, özel korumalı erişim değiştiricisini kullanarak, kapsayan sınıfı iç oluşturmanız gerekmeden aynı sonucu elde edebilirsiniz.  
  
## <a name="other-types"></a>Diğer türler  
 Bir ad alanı içinde doğrudan tanımlanmış arabirimler, genel veya iç olarak veya sınıflar ve yapılar gibi, varsayılan olarak dahili erişim için arabirimler olarak belirtilebilir. Arabirim üyeleri her zaman geneldir çünkü bir arabirimin amacı başka türlerin bir sınıfa veya yapıya erişmesine olanak sağlamaktır. Arabirim üyelerine erişim değiştiricileri uygulanamaz.  
  
 Numaralandırma üyeleri her zaman geneldir ve erişim değiştiricileri uygulanmaz.  
  
 Temsilciler sınıflar ve yapılar gibi davranır. Varsayılan olarak, bir ad alanı içinde doğrudan bildirildiği sırada iç erişimleri ve iç içe olduğunda özel erişim vardır.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Arabirimler](../interfaces/index.md)
- [private](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
- [internal](../../language-reference/keywords/internal.md)
- [protected](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/keywords/struct.md)
- [interface](../../language-reference/keywords/interface.md)
