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
ms.openlocfilehash: 6e6e9cc9210232059210862f2bda691c57b372d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353234"
---
# <a name="inherits-statement"></a>Inherits Deyimi
Geçerli sınıfın ya da arabirimin öznitelikleri, değişkenleri, özellikleri, yordamları ve olayları başka bir sınıf veya arabirim kümesinden devralmasını sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`basetypenames`|Gerekli. Bu sınıfın türetildiği sınıfın adı.<br /><br /> veya<br /><br /> Bu arabirimin türettiği arabirimlerin adları. Birden çok adı ayırmak için virgül kullanın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanıldıysa, `Inherits` deyimin bir sınıf veya arabirim tanımında ilk boş olmayan, yorum olmayan satırı olması gerekir. `Class` veya `Interface` deyiminizi hemen izlemelidir.  
  
 Yalnızca bir sınıf veya arabirimde `Inherits` kullanabilirsiniz. Bu, devralma için bildirim bağlamının kaynak dosya, ad alanı, yapı, modül, yordam veya blok olamayacağı anlamına gelir.  
  
## <a name="rules"></a>Kurallar  
  
- **Sınıf devralma.** Bir sınıf `Inherits` ifadesini kullanıyorsa yalnızca bir temel sınıf belirtebilirsiniz.  
  
     Bir sınıf, içinde iç içe geçmiş bir sınıftan devralınabilir.  
  
- **Arabirim devralma.** Bir arabirim `Inherits` ifadesini kullanıyorsa, bir veya daha fazla temel arabirim belirtebilirsiniz. Her biri aynı ada sahip bir üye tanımlasa bile iki arabirimden devralma yapabilirsiniz. Bunu yaparsanız, uygulama kodunun hangi üyeyi uygulamakta olduğunu belirtmek için ad nitelemesini kullanması gerekir.  
  
     Arabirim, daha kısıtlayıcı erişim düzeyine sahip başka bir arabirimden devralınabilir. Örneğin, bir `Public` arabirimi `Friend` arabiriminden devralınabilir.  
  
     Arabirim, içinde iç içe geçmiş bir arabirimden devralınabilir.  
  
 .NET Framework sınıf devralma örneği, <xref:System.SystemException> sınıfından devralan <xref:System.ArgumentException> sınıfıdır. Bu, <xref:System.Exception.Message%2A> özelliği ve <xref:System.Exception.ToString%2A> yöntemi gibi sistem özel durumları için gerekli tüm önceden tanımlanmış özellikleri ve yordamları <xref:System.ArgumentException> sağlar.  
  
 .NET Framework bir arabirim devralım örneği, <xref:System.Collections.IEnumerable> arabiriminden devralan <xref:System.Collections.ICollection> arabirimidir. Bu <xref:System.Collections.ICollection>, bir koleksiyonun çapraz geçişini yapmak için gereken Numaralandırıcı tanımını devralmasını sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `thisClass` adlı bir sınıfın `anotherClass`adlı bir temel sınıfın tüm üyelerini nasıl devralmasını göstermek için `Inherits` ifadesini kullanır.  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birden çok arabirimin devralınmasını gösterir.  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 `thisInterface` adlı arabirim artık, devralınan üyelerin,, ayrılmış kaynakları serbest bırakarak ve bir nesnenin değerini bir `String`ifade etmek için sırasıyla, <xref:System.IComparable>, <xref:System.IDisposable>ve <xref:System.IFormattable> arabirimlerinden tüm tanımları içerir. `thisInterface` uygulayan bir sınıf, her temel arabirimin her üyesini uygulamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
