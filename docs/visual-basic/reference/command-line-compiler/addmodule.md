---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: fbe3634d1fbc03acd56ef7276d65fd54493b9806
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002422"
---
# <a name="-addmodule"></a>-addmodule
Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Gerekli. Meta veri içeren ancak derleme bildirimleri içermeyen dosyaların virgülle ayrılmış listesi. Boşluk içeren dosya adları tırnak işaretleri ("") içine alınmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 parametresiyle listelenen dosyalar `-target:module` seçeneği ile oluşturulmalıdır ya da başka bir derleyicinin `-target:module` ' ye denk gelmelidir.  
  
 @No__t-0 ile eklenen tüm modüller, çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır. Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modülün çalışma zamanında uygulama dizininde olması gerekir. Değilse, @no__t 0 hatası alırsınız.  
  
 @No__t-2 ile `-target:module` dışında herhangi bir[hedef Visual Basic (](../../../visual-basic/reference/command-line-compiler/target.md) örtük veya açık) seçeneğini belirtirseniz, `-addmodule` ' e geçirdiğiniz dosyalar projenin derlemesinin bir parçası haline gelir. @No__t-0 ile eklenen bir veya daha fazla dosya içeren bir çıkış dosyası çalıştırmak için bütünleştirilmiş kod gereklidir.  
  
 Bütünleştirilmiş kod içeren bir dosyadan meta verileri içeri aktarmak için [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) kullanın.  
  
> [!NOTE]
> @No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bir modül oluşturur.  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 Aşağıdaki kod modülün türlerini içeri aktarır.  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 @No__t-0 ' ı çalıştırdığınızda `802` çıkışı yapılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
