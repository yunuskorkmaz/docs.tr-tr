---
title: "Kullanıcı Tanımlı Veri Türü"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e1876d61a2ce89b04c6e5061b868f0be365639f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="user-defined-data-type"></a>Kullanıcı Tanımlı Veri Türü
Veri tanımladığınız bir biçimde tutar. `Structure` Deyimi biçimini tanımlar.  
  
 Visual Basic önceki sürümleri, kullanıcı tanımlı tür (UDT) destekler. Geçerli sürümü için UDT genişletir bir *yapısı*. Bir veya daha fazla birleşimini yapısıdır *üyeleri* çeşitli veri türleri. Tek tek üyeleri erişebilirsiniz ancak Visual Basic bir yapı tek bir birim olarak değerlendirir.  
  
## <a name="remarks"></a>Açıklamalar  
 Çeşitli veri türleri tek bir birimde birleştirmek gerektiğinde ya da başlangıç veri türleri hiçbiri gereksinimlerinizi hizmet yapısı veri türünü kullanmak ve tanımlayın.  
  
 Varsayılan değer yapısı veri türünün her birinin üyelerine varsayılan değerlerin birleşimi oluşur.  
  
## <a name="declaration-format"></a>Bildirim biçimi  
 Yapı bildirimleri ile başlayan [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md) ve biten `End``Structure` deyimi. `Structure` Deyimi de yapısı tanımlama veri türünün tanımlayıcısıdır yapısı adı sağlar. Diğer kod parçalarını bildirme değişkenleri ve parametreleri işlevi dönüş değerleri bu yapısı veri türüne sahip olması için bu tanımlayıcı kullanabilirsiniz.  
  
 Bildirimler arasında `Structure` ve `End``Structure` deyimleri yapısı üyeleri tanımlayın.  
  
## <a name="member-access-levels"></a>Üye erişim düzeyleri  
 Kullanarak her üye bildirmelidir bir [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md) veya erişim düzeyi gibi belirten bir ifade [ortak](../../../visual-basic/language-reference/modifiers/public.md), [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md), veya [özel](../../../visual-basic/language-reference/modifiers/private.md). Kullanırsanız, bir `Dim` deyimi, public erişim düzeyi varsayılanlara.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Bellek tüketimi.** Tüm bileşik veri türleri gibi güvenli bir şekilde birbirine üyeleri nominal depolama ayrılmasını ekleyerek bir yapı toplam bellek tüketimi hesaplanamıyor. Ayrıca, depolama bellekte sırasını siparişinizi bildirimiyle aynı olduğunu güvenle varsayalım olamaz. Bir yapı depolama düzenini denetlemeye ihtiyacınız varsa, uygulamadan <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğini `Structure` deyimi.  
  
-   **Birlikte çalışma hakkında dikkat edilecek noktalar** Örneğin .NET Framework yazılmaz bileşenleriyle arabirim, Otomasyon veya COM nesneleri, kullanıcı tanımlı türler diğer ortamlarda Visual Basic ile uyumlu olmadığını unutmayın türlerini yapılandırın.  
  
-   **Genişletme.** Otomatik dönüştürme için veya herhangi bir yapı veri türü var. Dönüştürme işleçleri kullanarak yapısı üzerinde tanımlayabilirsiniz [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md), ve olacak şekilde her dönüşüm işleci bildirebilir `Widening` veya `Narrowing`.  
  
-   **Karakterleri yazın.** Değişmez değer türü karakteri ya da tanımlayıcı türü karakteri yapısı veri türlerine sahip.  
  
-   **Framework türü.** .NET Framework karşılık gelen türü yok. Tüm yapıları .NET Framework sınıfından <xref:System.ValueType?displayProperty=nameWithType>, ancak hiçbir tek tek yapısı karşılık gelen <xref:System.ValueType?displayProperty=nameWithType>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneği bir yapı bildirimi özetini gösterir.  
  
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
 [Veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Genişletme](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Daraltma](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Yapıları](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Veri türlerinin etkili kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
