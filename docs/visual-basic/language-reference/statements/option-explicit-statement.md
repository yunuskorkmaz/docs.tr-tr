---
title: Option Explicit Deyimi
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
ms.openlocfilehash: 44bf8205ec071710ee3660968ab3c3e9af33f74d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874937"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit Deyimi (Visual Basic)

Bir dosyadaki tüm değişkenlerin açık bildirimini zorlar veya değişken örtülü bildirimlere izin verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Bölümler  

 `On`  
 İsteğe bağlı. Denetlemeye izin vermez `Option Explicit` . `On`Veya `Off` belirtilmemişse, varsayılan olur `On` .  
  
 `Off`  
 İsteğe bağlı. Denetlemeyi devre dışı bırakır `Option Explicit` .  
  
## <a name="remarks"></a>Açıklamalar  

 `Option Explicit On`Ya da `Option Explicit` bir dosyada göründüğünde, ya da deyimlerini kullanarak tüm değişkenleri açıkça bildirmeniz gerekir `Dim` `ReDim` . Bildirilmemiş bir değişken adı kullanmaya çalışırsanız, derleme zamanında bir hata oluşur. `Option Explicit Off`İfade, değişkenlerin örtük bildirimine izin verir.  
  
 Kullanıldıysa, `Option Explicit` deyimi diğer kaynak kodu deyimlerinden önce bir dosyada görünmelidir.  
  
> [!NOTE]
> Ayarı `Option Explicit` `Off` , genellikle iyi bir uygulamadır. Bir veya daha fazla konumda değişken adı yanlış yazdığınızda, program çalıştırıldığında beklenmedik sonuçlara neden olabilir.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Açık bir seçenek Ifade yoksa  

 Kaynak kodu bir `Option Explicit` ifade içermiyorsa, derleme sayfasındaki **Açık ayar seçeneği** , [Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. Komut satırı derleyicisi kullanılırsa [-OptionExplicit](../../reference/command-line-compiler/optionexplicit.md) derleyici seçeneği kullanılır.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>IDE 'de Option Explicit ayarlamak için  
  
1. **Çözüm Gezgini**bir proje seçin. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Derle** sekmesine tıklayın.  
  
3. **Açık** kutuda değeri ayarlayın.  
  
 Yeni bir proje oluşturduğunuzda, **Derle** sekmesindeki **Açık ayar seçeneği** , **vb varsayılanlar** iletişim kutusunda **Açık seçenek** ayarı olarak ayarlanır. **Vb Varsayılanları** iletişim kutusuna erişmek Için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb** varsayılan olarak ilk varsayılan ayar `On` .  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Komut satırında Explicit seçeneğini ayarlamak için  
  
- **Vbc** komutuna [-OptionExplicit](../../reference/command-line-compiler/optionexplicit.md) derleyici seçeneğini ekleyin.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Option Explicit` tüm değişkenlerin açık bildirimini zorlamak için bildirimini kullanır. Bildirilmemiş bir değişkeni kullanma girişimi, derleme sırasında hataya neden olur.  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](dim-statement.md)
- [ReDim Deyimi](redim-statement.md)
- [Option Compare Deyimi](option-compare-statement.md)
- [Option Strict Deyimi](option-strict-statement.md)
- [-optioncompare](../../reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../reference/command-line-compiler/optionstrict.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
