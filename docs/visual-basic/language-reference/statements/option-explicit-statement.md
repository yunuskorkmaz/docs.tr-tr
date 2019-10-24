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
ms.openlocfilehash: 0405814efecbdff5769af36b27dce1cd3305aab5
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775491"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit Deyimi (Visual Basic)
Bir dosyadaki tüm değişkenlerin açık bildirimini zorlar veya değişken örtülü bildirimlere izin verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Bölümler  
 `On`  
 İsteğe bağlı. @No__t_0 denetlemeye izin vermez. @No__t_0 veya `Off` belirtilmemişse, varsayılan olarak `On`.  
  
 `Off`  
 İsteğe bağlı. @No__t_0 denetlemesini devre dışı bırakır.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dosyada `Option Explicit On` veya `Option Explicit` göründüğünde, `Dim` veya `ReDim` deyimlerini kullanarak tüm değişkenleri açıkça bildirmeniz gerekir. Bildirilmemiş bir değişken adı kullanmaya çalışırsanız, derleme zamanında bir hata oluşur. @No__t_0 bildirimi, değişkenlerin örtük bildirimine izin verir.  
  
 Kullanıldıysa, `Option Explicit` deyimi herhangi bir diğer kaynak kodu deyiminden önce bir dosyada yer almalıdır.  
  
> [!NOTE]
> @No__t_0 `Off` ayarı genellikle iyi bir uygulamadır. Bir veya daha fazla konumda değişken adı yanlış yazdığınızda, program çalıştırıldığında beklenmedik sonuçlara neden olabilir.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Açık bir seçenek Ifade yoksa  
 Kaynak kodu `Option Explicit` bir ifade içermiyorsa, derleme sayfasındaki **Açık ayar seçeneği** , [proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. Komut satırı derleyicisi kullanılırsa [-OptionExplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneği kullanılır.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>IDE 'de Option Explicit ayarlamak için  
  
1. **Çözüm Gezgini**bir proje seçin. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Derle** sekmesine tıklayın.  
  
3. **Açık** kutuda değeri ayarlayın.  
  
 Yeni bir proje oluşturduğunuzda, **Derle** sekmesindeki **Açık ayar seçeneği** , **vb varsayılanlar** iletişim kutusunda **Açık seçenek** ayarı olarak ayarlanır. **Vb Varsayılanları** iletişim kutusuna erişmek Için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb Varsayılanları** içindeki ilk varsayılan ayar `On`.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Komut satırında Explicit seçeneğini ayarlamak için  
  
- **Vbc** komutuna [-OptionExplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneğini ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm değişkenlerin açık bildirimini zorlamak için `Option Explicit` bildirimini kullanır. Bildirilmemiş bir değişkeni kullanma girişimi, derleme sırasında hataya neden olur.  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
- [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Option Compare Deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
