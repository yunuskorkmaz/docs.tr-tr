---
title: Inherits Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 43a8aa4e9e04ee035cb52e9f829de13e5c022217
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="inherits-statement"></a>Inherits Deyimi
Geçerli sınıf veya başka bir sınıf veya arabirim kümesine öznitelikleri, değişkenleri, özellikleri, yordamlar ve olayları devralmak için arabirimi neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`basetypenames`|Gerekli. Bu sınıf türetilen sınıfın adı.<br /><br /> -veya-<br /><br /> Bu arabirim türetilen arabirimleri adları. Birden çok ad ayırmak için virgül kullanın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullandıysanız, `Inherits` deyimi bir sınıf veya arabirim tanımı ilk boş olmayan ve yorum olmayan satır olması gerekir. Hemen izlemeniz gereken `Class` veya `Interface` deyimi.  
  
 Kullanabileceğiniz `Inherits` yalnızca bir sınıf veya arabirim olarak. Başka bir deyişle, bir devralma bildirimi bağlamının bir kaynak dosyasını, ad alanı, yapısı, modülü, yordam veya blok olamaz.  
  
## <a name="rules"></a>Kurallar  
  
-   **Sınıf devralma.** Bir sınıf kullanıyorsa `Inherits` deyimi, yalnızca bir taban sınıf belirtin.  
  
     Bir sınıf içinde iç içe bir sınıftan devralınan olamaz.  
  
-   **Devralma arabirim.** Arabirim kullanıyorsa `Inherits` deyimi, bir veya daha fazla temel arabirimleri belirtebilirsiniz. Bunların hepsi aynı ada sahip bir üye tanımlayın olsa bile, iki arabirimlerinden devralabilirsiniz. Bunu yapmak, uygulama kodu ad niteliği uyguladığı hangi üye belirtmek için kullanmanız gerekir.  
  
     Bir arabirim daha kısıtlayıcı erişim düzeyine sahip başka bir arabirim devralınmalıdır olamaz. Örneğin, bir `Public` olamaz arabirimi devralan bir `Friend` arabirimi.  
  
     Bir arabirim içinde iç içe bir arabirimden devralan olamaz.  
  
 .NET Framework sınıf devralma örneğidir <xref:System.ArgumentException> devraldığı sınıfı <xref:System.SystemException> sınıfı. Bu sağlayan <xref:System.ArgumentException> tüm gibi gerekli sistem durumlarını tarafından yordamlar ve önceden tanımlanmış özellikler <xref:System.Exception.Message%2A> özelliği ve <xref:System.Exception.ToString%2A> yöntemi.  
  
 .NET Framework'teki arabirimi devralma örneğidir <xref:System.Collections.ICollection> devraldığı arabirimi <xref:System.Collections.IEnumerable> arabirimi. Bu neden <xref:System.Collections.ICollection> koleksiyonu geçiş için gereken Numaralandırıcı tanımını devralmak için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Inherits` nasıl adlı bir sınıf göstermek için deyimi `thisClass` adlı bir taban sınıfın tüm üyeleri devrettiği `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birden çok arabirimlerinin devralma gösterir.  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 Adlı arabirim `thisInterface` artık tüm tanımlarında içerir <xref:System.IComparable>, <xref:System.IDisposable>, ve <xref:System.IFormattable> devralınan üyeleri sağlamak sırasıyla iki nesne türüne özgü karşılaştırma için serbest arabirimleri ayrılan kaynaklar ve bir nesne olarak değeri ifade bir `String`. Uygulayan bir sınıf `thisInterface` her üyesinin her temel arabirimi uygulamalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
