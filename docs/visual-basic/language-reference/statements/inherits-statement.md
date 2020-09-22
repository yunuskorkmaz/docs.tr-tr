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
ms.openlocfilehash: dd8fbc71fdc859bb127764951464278267c0984c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875224"
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
|`basetypenames`|Gereklidir. Bu sınıfın türetildiği sınıfın adı.<br /><br /> -veya-<br /><br /> Bu arabirimin türettiği arabirimlerin adları. Birden çok adı ayırmak için virgül kullanın.|  
  
## <a name="remarks"></a>Açıklamalar  

 Kullanıldıysa, `Inherits` bir sınıf veya arabirim tanımında deyimin ilk boş olmayan, yorum olmayan satırı olması gerekir. Hemen `Class` veya `Interface` ifadesini izlemelidir.  
  
 `Inherits`Yalnızca bir sınıf veya arabirim için kullanabilirsiniz. Bu, devralma için bildirim bağlamının kaynak dosya, ad alanı, yapı, modül, yordam veya blok olamayacağı anlamına gelir.  
  
## <a name="rules"></a>Kurallar  
  
- **Sınıf devralma.** Bir sınıf, ifadesini kullanıyorsa `Inherits` yalnızca bir temel sınıf belirtebilirsiniz.  
  
     Bir sınıf, içinde iç içe geçmiş bir sınıftan devralınabilir.  
  
- **Arabirim devralma.** Bir arabirim, ifadesini kullanıyorsa `Inherits` , bir veya daha fazla temel arabirim belirtebilirsiniz. Her biri aynı ada sahip bir üye tanımlasa bile iki arabirimden devralma yapabilirsiniz. Bunu yaparsanız, uygulama kodunun hangi üyeyi uygulamakta olduğunu belirtmek için ad nitelemesini kullanması gerekir.  
  
     Arabirim, daha kısıtlayıcı erişim düzeyine sahip başka bir arabirimden devralınabilir. Örneğin, bir `Public` arabirim `Friend` arabiriminden devralınabilir.  
  
     Arabirim, içinde iç içe geçmiş bir arabirimden devralınabilir.  
  
 .NET Framework sınıf devralma örneği <xref:System.ArgumentException> , sınıfından devralan sınıftır <xref:System.SystemException> . Bu, <xref:System.ArgumentException> özelliği ve yöntemi gibi sistem özel durumları için gerekli tüm önceden tanımlanmış özellikleri ve yordamları sağlar <xref:System.Exception.Message%2A> <xref:System.Exception.ToString%2A> .  
  
 .NET Framework arabirim devralım örneği <xref:System.Collections.ICollection> arabiriminden devralan arabirimdir <xref:System.Collections.IEnumerable> . Bu, <xref:System.Collections.ICollection> bir koleksiyonun çapraz geçişini yapmak için gereken Numaralandırıcı tanımını devralmasını sağlar.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, adlı `Inherits` bir sınıfın `thisClass` adlı bir temel sınıfın tüm üyelerini nasıl devralmasını göstermek için ifadesini kullanır `anotherClass` .  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, birden çok arabirimin devralınmasını gösterir.  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 Artık adlı arabirim,, `thisInterface` ve ' deki tüm tanımları içerir, <xref:System.IComparable> <xref:System.IDisposable> ve <xref:System.IFormattable> devralınan üyelerin, iki nesnenin türüne özgü karşılaştırmasına, ayrılan kaynakları serbest bırakarak ve bir nesnenin değerini olarak ifade eder `String` . Uygulayan bir sınıf `thisInterface` , her temel arabirimin her üyesini uygulamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [MustInherit](../modifiers/mustinherit.md)
- [NotInheritable](../modifiers/notinheritable.md)
- [Nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md)
- [Devralma Temelleri](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Arabirimler](../../programming-guide/language-features/interfaces/index.md)
