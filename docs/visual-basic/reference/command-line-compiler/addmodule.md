---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 5a6d367f4b09de600bb744aa2abed0da2c93aa0b
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202372"
---
# <a name="-addmodule"></a>-addmodule
Derleyicinin tüm kullanılabilir belirtilen dosyalar, şu anda derlemekte olduğunuz projeye kullandırmasına bilgileri yazın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Gerekli. Meta veriler içerir, ancak derleme bildirimleri içermeyen dosyaları virgülle ayrılmış liste. Boşluk içeren dosya adları tırnak işaretleri arasına ("").  
  
## <a name="remarks"></a>Açıklamalar  
 Tarafından listelenen dosyaların `fileList` parametresi ile oluşturulmalıdır `-target:module` seçeneğini veya başka bir derleyicinin eşdeğer `-target:module`.  
  
 İle eklenen tüm modüller `-addmodule` çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır. Diğer bir deyişle, bir modül herhangi bir dizinde derleme zamanında belirtebilirsiniz, ancak modülü, çalışma zamanında uygulama dizininde olması gerekir. Yüklü değilse, size bir <xref:System.TypeLoadException> hata.  
  
 (Örtük veya açık) belirtirseniz herhangi[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) dışında seçeneği `-target:module` ile `-addmodule`, geçireceğiniz dosyaları `-addmodule` projenin derlemenin parçası haline gelir. Bir derleme varsa bir çıktı dosyası çalıştırmak için gerekli olan veya daha fazla dosya ile eklenen `-addmodule`.  
  
 Kullanım [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) bir derlemeyi içeren bir dosyanın meta verilerini almak için.  
  
> [!NOTE]
>  `-addmodule` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir modül oluşturur.  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 Aşağıdaki kod modülün türleri içeri aktarır.  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 Çalıştırdığınızda `t1`, bu çıkışları `802`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
