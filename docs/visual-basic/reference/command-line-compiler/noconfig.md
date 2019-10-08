---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: c57ed1699d110959e9faf3dc3d43bcc200851c1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005438"
---
# <a name="-noconfig"></a>-noconfig
Derleyicinin yaygın olarak kullanılan .NET Framework derlemelerine otomatik olarak başvurmamalıdır veya `System` ve `Microsoft.VisualBasic` ad alanlarını içeri aktaramamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 seçeneği derleyiciye, vbc. exe dosyası ile aynı dizinde bulunan Vbc. rsp dosyası ile derlenmeyeceğini söyler. Vbc. rsp dosyası, yaygın olarak kullanılan .NET Framework derlemelerine başvurur ve `System` ve `Microsoft.VisualBasic` ad alanlarını içeri aktarır. @No__t-0 seçeneği belirtilmediği takdirde derleyici System. dll derlemesine dolaylı olarak başvurur. @No__t-0 seçeneği, derleyicinin Vbc. rsp ile derlenmeyeceğini veya System. dll derlemesine otomatik olarak başvurmayacağını söyler.  
  
> [!NOTE]
> Mscorlib. dll ve Microsoft. VisualBasic. dll derlemelerine her zaman başvurulur.  
  
 Vbc. rsp dosyasını, her Vbc. exe derlemesine dahil edilecek ek derleyici seçeneklerini belirtmek için değiştirebilirsiniz (`-noconfig` seçeneği belirtildiğinde hariç). Daha fazla bilgi için bkz. [@ (yanıt dosyası belirtme)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Derleyici en son `vbc` komutuna geçirilen seçenekleri işler. Bu nedenle, komut satırındaki herhangi bir seçenek, vbc. rsp dosyasında aynı seçeneğin ayarını geçersiz kılar.  
  
> [!NOTE]
> @No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (Yanıt Dosyasını Belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
