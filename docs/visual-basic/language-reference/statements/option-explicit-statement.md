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
ms.openlocfilehash: 3a2d81b1441052c132e4739dfe6045f8c3a026d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604607"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit Deyimi (Visual Basic)
Bir dosyadaki tüm değişkenlerin açıkça bildirilmesini zorlar veya değişkenlerin örtük bildirimleri sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Bölümler  
 `On`  
 İsteğe bağlı. Etkinleştirir `Option Explicit` denetleniyor. Varsa `On` veya `Off` belirtilmezse, varsayılan `On`.  
  
 `Off`  
 İsteğe bağlı. Devre dışı bırakır `Option Explicit` denetleniyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman `Option Explicit On` veya `Option Explicit` görünür bir dosyada, açıkça bildirmelidir tüm değişkenleri kullanarak `Dim` veya `ReDim` deyimleri. Bildirilmemiş bir değişken adı kullanmayı denerseniz, derleme zamanı sırasında bir hata oluşur. `Option Explicit Off` Deyimi değişkenlerin örtük bildirimi sağlar.  
  
 Kullandıysanız, `Option Explicit` ifadesi, başka bir kaynak kod deyimleri önce bir dosyada görünmelidir.  
  
> [!NOTE]
>  Ayarı `Option Explicit` için `Off` genellikle iyi bir uygulama değildir. Bir değişken adı konumlarda programını çalıştırdığınızda, beklenmeyen sonuçlara neden olacağından bir veya daha fazla hata hatalı.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Ne zaman Option Explicit deyimi mevcut değil  
 Kaynak kodu içermiyorsa bir `Option Explicit` deyimi, **Option Explicit** ayarı [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. Komut satırı derleyicisi kullanılırsa, [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneği kullanılır.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>Option Explicit IDE'de ayarlamak için  
  
1.  İçinde **Çözüm Gezgini**, bir proje seçin. Üzerinde **proje** menüsünde tıklatın **özellikleri**.  
  
2.  Tıklatın **derleme** sekmesi.  
  
3.  Değer kümesinde **Option Explicit** kutusu.  
  
 Yeni bir proje oluşturduğunuzda **Option Explicit** ayarı **derleme** sekmesini ayarlanmış **Option Explicit** ayarı **VB varsayılanları**iletişim kutusu. Erişim için **VB varsayılan olarak** iletişim kutusundaki **Araçları** menüsünde tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda, genişletin **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarı **VB varsayılanları** olan `On`.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Option Explicit komut satırında ayarlamak için  
  
-   Dahil [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneği **vbc** komutu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Option Explicit` tüm değişkenlerin açıkça bildirilmesini zorlamak için deyimi. Bildirilmemiş bir değişkeni kullanılmaya çalışılıyor derleme zamanında bir hataya neden olur.  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Option Compare Deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
