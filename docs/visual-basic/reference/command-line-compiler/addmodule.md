---
title: -addmodule
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c17d5541fe2d02ba88f4c5ef259b2248f371dfe5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
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
