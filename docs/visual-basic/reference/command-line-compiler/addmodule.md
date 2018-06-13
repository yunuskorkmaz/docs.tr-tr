---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2fefdf81ab25d2e109f265f0c895a3415ad5673d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656012"
---
# <a name="-addmodule"></a>-addmodule
Tüm hale getirmesine neden olur. şu anda derlediğiniz proje için belirtilen dosya veya dosyalar kullanılabilir bilgileri yazın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Gerekli. Meta veriler içeren ancak derleme bildirimlerinin içermeyen dosyaları virgülle ayrılmış listesi. Boşluk içeren dosya adları tırnak işaretleri arasına ("").  
  
## <a name="remarks"></a>Açıklamalar  
 Tarafından listelenen dosyaları `fileList` parametresi ile oluşturulmalıdır `-target:module` seçeneğini veya başka bir derleyicinin eşdeğer ile `-target:module`.  
  
 İle eklenen tüm modüller `-addmodule` çalışma zamanında çıktı dosyası ile aynı dizinde olmalıdır. Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modül çalışma zamanında uygulama dizininde olmalıdır. Değilse, size bir <xref:System.TypeLoadException> hata.  
  
 (Örtük veya açık olarak) belirtirseniz, tüm[-hedef (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) dışında seçeneği `-target:module` ile `-addmodule`, geçireceğiniz dosyaları `-addmodule` projenin derleme bir parçası haline gelir. Bir derlemeyi varsa bir çıktı dosyasını çalıştırmak için gerekli ya da daha fazla dosya eklendi `-addmodule`.  
  
 Kullanım [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) bir derleme içeren dosyadan meta verileri.  
  
> [!NOTE]
>  `-addmodule` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bir modül oluşturur.  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 Aşağıdaki kod modülün türlerini alır.  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 Çalıştırdığınızda `t1`, onu çıkarır `802`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
