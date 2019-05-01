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
ms.openlocfilehash: 0a319ba4259e66ed9a37aa2de9e97d2335b78663
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784052"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit Deyimi (Visual Basic)
Bir dosyadaki tüm değişkenleri açık bildirimini zorlar ya da örtük değişkenler bildirimleri sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Bölümler  
 `On`  
 İsteğe bağlı. Sağlar `Option Explicit` denetleniyor. Varsa `On` veya `Off` belirtilmezse, varsayılan `On`.  
  
 `Off`  
 İsteğe bağlı. Devre dışı bırakır `Option Explicit` denetleniyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman `Option Explicit On` veya `Option Explicit` gerekir açıkça bildirdiğiniz tüm değişkenleri kullanarak bir dosyada görünür `Dim` veya `ReDim` deyimleri. Bildirilmemiş bir değişken adını kullanmayı denerseniz, derleme sırasında bir hata oluşur. `Option Explicit Off` İfadesi örtük bir değişken bildirimi sağlar.  
  
 Kullandıysanız, `Option Explicit` deyimi, bir dosyada başka bir kaynak kod deyimlerini önce görünmelidir.  
  
> [!NOTE]
>  Ayarı `Option Explicit` için `Off` genellikle iyi bir uygulama değildir. Bir değişken adı program çalıştırıldığında bu beklenmeyen sonuçlara neden olduğu bir veya daha fazla konumda yazsanız.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Ne zaman Option Explicit deyimi mevcut değil  
 Kaynak kodu içermiyorsa bir `Option Explicit` deyimi **Option Explicit** ayarını [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. Komut satırı derleyicisini kullanılıyorsa [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneği kullanılır.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>Option Explicit IDE içinde ayarlamak için  
  
1. İçinde **Çözüm Gezgini**, bir proje seçin. Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
2. Tıklayın **derleme** sekmesi.  
  
3. Değer kümesindeki **Option Explicit** kutusu.  
  
 Yeni bir proje oluşturduğunuzda **Option Explicit** ayarını **derleme** sekmesinde ayarlanmış **Option Explicit** ayarı **VB varsayılanları**iletişim kutusu. Erişim için **VB varsayılanları** iletişim kutusundaki **Araçları** menüsünde tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarda **VB varsayılanları** olduğu `On`.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Option Explicit komut satırında ayarlamak için  
  
- Dahil [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneğini **vbc** komutu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Option Explicit` tüm değişkenleri açık bildirimini zorlamak için deyimi. Bildirilmemiş bir değişken kullanılmaya çalışılıyor derleme zamanında bir hataya neden olur.  
  
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
