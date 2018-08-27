---
title: Inherits deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 4a98ada39a04730b46f40fe139e72d1855d9b067
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931241"
---
# <a name="inherits-statement"></a>Inherits Deyimi
Geçerli sınıfın ya da arabirimin öznitelikleri, değişkenleri, özellikleri, yordamları ve olayları başka bir sınıf veya arabirim kümesini devralan neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`basetypenames`|Gerekli. Bu sınıfın türetildiği sınıfın adı.<br /><br /> veya<br /><br /> Bu arabirim türetildiği arayüzlerin adları. Birden çok adını ayırmak için virgül kullanın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullandıysanız, `Inherits` deyimi, bir sınıf veya arabirim tanımı ilk boş olmayan, olmayan açıklama satırı olmalıdır. Hemen izlemelidir `Class` veya `Interface` deyimi.  
  
 Kullanabileceğiniz `Inherits` yalnızca bir sınıf veya arabirim olarak. Başka bir deyişle, bir devralma için bildirim içeriğinin bir kaynak dosyası, ad alanı, yapı, modül, yordam veya blok olamaz.  
  
## <a name="rules"></a>Kurallar  
  
-   **Sınıf devralma.** Bir sınıf kullanıyorsa `Inherits` deyimi, yalnızca bir temel sınıf belirtebilirsiniz.  
  
     Bir sınıf içinde iç içe geçmiş bir sınıfı devralamaz.  
  
-   **Devralma arabirim.** Bir arabirim kullanıyorsa `Inherits` deyimi, bir veya daha fazla temel arabirimde belirtebilirsiniz. Bunların hepsi aynı ada sahip bir üye tanımlarsanız bile iki ara birimden devralınabilir. Bunu yaparsanız uyguladığı üye belirtmek için uygulanan kodun ad niteliği kullanmanız gerekir.  
  
     Bir arabirim daha kısıtlayıcı bir erişim düzeyi olan başka bir arabirimden devralamaz. Örneğin, bir `Public` arabirimi öğesinden özellik devralamaz bir `Friend` arabirimi.  
  
     Bir arabirim, kendi içinde iç içe bir arabirimden devralamaz.  
  
 .NET Framework içinde sınıf Devralmanın örneğidir <xref:System.ArgumentException> öğesinden devralan sınıf <xref:System.SystemException> sınıfı. Bu sağlayan <xref:System.ArgumentException> önceden tanımlanmış özellikler ve yordamlar gibi sistem özel durumların gerekli <xref:System.Exception.Message%2A> özelliği ve <xref:System.Exception.ToString%2A> yöntemi.  
  
 .NET Framework'teki arabirimi devralma örneğidir <xref:System.Collections.ICollection> öğesinden devralan bir arayüzü <xref:System.Collections.IEnumerable> arabirimi. Bu neden <xref:System.Collections.ICollection> bir koleksiyonu geçirmek için gereken Numaralandırıcı tanımını devralmak için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Inherits` nasıl adlı bir sınıf gösterilecek deyimi `thisClass` adlı bir temel sınıf tüm üyelerini devralabilir `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birden çok arabirim devralma gösterir.  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 Adlı arabirim `thisInterface` artık tüm tanımlar içeren <xref:System.IComparable>, <xref:System.IDisposable>, ve <xref:System.IFormattable> devralınan üyeleri sağlamak sırasıyla iki nesne, türe özgü karşılaştırma için serbest arabirimleri ayrılan kaynaklar ve bir nesne olarak değerini ifade bir `String`. Uygulayan bir sınıf `thisInterface` her üyesi temel her arabirimi uygulamalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
