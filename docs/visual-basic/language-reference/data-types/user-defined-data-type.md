---
title: Kullanıcı tanımlı veri türü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 1dac93145b6e11a0d149f03b43e1e0b28b770925
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342283"
---
# <a name="user-defined-data-type"></a>Kullanıcı Tanımlı Veri Türü
Tanımladığınız bir biçimde verileri tutar. `Structure` Biçimini tanımlar.  
  
 Visual Basic'in önceki sürümlerindeki kullanıcı tanımlı tür (UDT) destekler. Geçerli sürümü için UDT genişleyen bir *yapısı*. Bir yapının bir veya daha fazla bir bitiştirmedir *üyeleri* çeşitli veri türleri. Visual Basic bir yapı üyelerinin tek tek erişebilirsiniz ancak tek bir birim olarak ele alır.  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımlamak ve bir yapı veri türü, çeşitli veri türlerini tek bir birimde birleştirebilirsiniz ihtiyacınız olduğunda ya da hiçbiri başlangıç veri türleri ihtiyaçlarınızı karşılamak kullanın.  
  
 Bir yapı veri türünün varsayılan değeri, her üyenin varsayılan değerlerinin birleşimi oluşur.  
  
## <a name="declaration-format"></a>Bildirim biçimi  
 Yapı bildirimleri ile başlayan [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md) ve ile sona eren `End Structure` deyimi. `Structure` Deyimi ayrıca veri türünün yapısını tanımlama tanımlayıcıdır yapının adını sağlar. Kodun diğer bölümleri bu tanımlayıcı değerleri bu yapının veri türünde olmasını değişkenleri, parametreler ve işlev dönüş bildirmek için kullanabilirsiniz.  
  
 Bildirimler arasında `Structure` ve `End Structure` deyimi yapının üyeleri tanımlar.  
  
## <a name="member-access-levels"></a>Üye erişim düzeyleri  
 Kullanarak her üyesini bildirmeniz gerekir bir [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md) veya erişim düzeyi gibi belirten bir deyimi [genel](../../../visual-basic/language-reference/modifiers/public.md), [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md), veya [özel](../../../visual-basic/language-reference/modifiers/private.md). Kullanıyorsanız bir `Dim` deyimi, genel erişim düzeyi varsayılanlara.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Bellek tüketimi.** Tüm bileşik veri türleri gibi ile güvenli bir şekilde, üyelerinin nominal depolama ayırmalarını birlikte ekleyerek bir yapının toplam bellek tüketimini hesaplanamaz. Ayrıca, siparişin bellekteki depolama sırasının bildirim ile aynı olduğunu güvenli bir şekilde varsayamazsınız. Bir yapının depolama düzenini denetlemek için ihtiyacınız varsa, uygulayabilirsiniz <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğini `Structure` deyimi.  
  
-   **Birlikte çalışabilirlik değerlendirmeleri.** Örneğin, .NET Framework için yazılmaz bileşenleriyle arabirim, otomasyon ve COM nesneleri, kullanıcı tanımlı türler diğer ortamlarda Visual Basic ile uyumlu olmadığını unutmayın türlerini yapılandırın.  
  
-   **Genişletme.** Otomatik dönüştürme için veya herhangi bir yapı veri türü yoktur. Dönüştürme işleçleri, yapısını kullanarak tanımlayabileceğiniz [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md), ve her dönüştürme işleci olmasını bildirebilirsiniz `Widening` veya `Narrowing`.  
  
-   **Tür karakterleri.** Değişmez değer türü karakteri ya da tanımlayıcı türü karakteri yapısı veri türleri vardır.  
  
-   **Çerçeve türü.** .NET Framework içinde karşılık gelen türü yoktur. Tüm yapıları .NET Framework sınıfından <xref:System.ValueType?displayProperty=nameWithType>, ancak tek tek hiçbir yapısına karşılık gelen <xref:System.ValueType?displayProperty=nameWithType>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki paradigma, bir yapının bildirimi özetini gösterir.  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ValueType>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
