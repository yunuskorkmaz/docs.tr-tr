---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2de5fe82f1969a2fdb305d45951d7d698252c0c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61839228"
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
