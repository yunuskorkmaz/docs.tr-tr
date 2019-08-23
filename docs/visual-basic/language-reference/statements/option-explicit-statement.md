---
title: Option Explicit Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
ms.openlocfilehash: c027964d185d7f69c0a56a4386bedc2d8f9d2eac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912331"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit Deyimi (Visual Basic)
Bir dosyadaki tüm değişkenlerin açık bildirimini zorlar veya değişken örtülü bildirimlere izin verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Bölümler  
 `On`  
 İsteğe bağlı. Denetlemeye `Option Explicit` izin vermez. Veya belirtilmemişse, varsayılan olur `On`. `On` `Off`  
  
 `Off`  
 İsteğe bağlı. Denetlemeyi `Option Explicit` devre dışı bırakır.  
  
## <a name="remarks"></a>Açıklamalar  
 Ya da bir dosyada göründüğünde, ya `ReDim` da `Dim` deyimlerini kullanarak tüm değişkenleri açıkça bildirmeniz gerekir. `Option Explicit` `Option Explicit On` Bildirilmemiş bir değişken adı kullanmaya çalışırsanız, derleme zamanında bir hata oluşur. İfade `Option Explicit Off` , değişkenlerin örtük bildirimine izin verir.  
  
 Kullanıldıysa, `Option Explicit` deyimi diğer kaynak kodu deyimlerinden önce bir dosyada görünmelidir.  
  
> [!NOTE]
> Ayarı `Option Explicit`,genellikleiyi biruygulamadır.`Off` Bir veya daha fazla konumda değişken adı yanlış yazdığınızda, program çalıştırıldığında beklenmedik sonuçlara neden olabilir.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Açık bir seçenek Ifade yoksa  
 Kaynak kodu bir `Option Explicit` ifade içermiyorsa, derleme sayfasındaki **Açık ayar seçeneği** , [Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. Komut satırı derleyicisi kullanılırsa, [/OptionExplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneği kullanılır.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>IDE 'de Option Explicit ayarlamak için  
  
1. **Çözüm Gezgini**bir proje seçin. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Derle** sekmesine tıklayın.  
  
3. **Açık** kutuda değeri ayarlayın.  
  
 Yeni bir proje oluşturduğunuzda, **Derle** sekmesindeki **Açık ayar seçeneği** , **vb varsayılanlar** iletişim kutusunda **Açık seçenek** ayarı olarak ayarlanır. **Vb Varsayılanları** iletişim kutusuna erişmek Için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. Vb`On`varsayılan olarak ilk varsayılan ayar.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Komut satırında Explicit seçeneğini ayarlamak için  
  
- **Vbc** komutuna [/OptionExplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneğini ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Option Explicit` tüm değişkenlerin açık bildirimini zorlamak için bildirimini kullanır. Bildirilmemiş bir değişkeni kullanma girişimi, derleme sırasında hataya neden olur.  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
- [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Option Compare Deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
