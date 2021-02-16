---
description: :-Noconfig hakkında daha fazla bilgi edinin
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: e97d44427b537e73a404a47d30db202e2c3b1f41
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481694"
---
# <a name="-noconfig"></a>-noconfig

Derleyicinin yaygın olarak kullanılan .NET Framework derlemelerine otomatik olarak başvurmamalıdır veya `System` ve ad alanlarını içeri aktaramamalıdır `Microsoft.VisualBasic` .  
  
## <a name="syntax"></a>Syntax  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Açıklamalar  

 `-noconfig`Seçeneği, derleyicinin Vbc.exe dosyasıyla aynı dizinde bulunan Vbc. rsp dosyası ile derlenmeyeceğini söyler. Vbc. rsp dosyası, yaygın olarak kullanılan .NET Framework derlemelerine başvurur ve `System` ve `Microsoft.VisualBasic` ad alanlarını içeri aktarır. Seçenek belirtilmediği takdirde derleyici System.dll derlemesine örtülü olarak başvurur `-nostdlib` . `-nostdlib`Seçeneği, derleyicinin Vbc. rsp ile derlenmeyeceğini veya System.dll derlemesine otomatik olarak başvurmayacağını söyler.  
  
> [!NOTE]
> Mscorlib.dll ve Microsoft.VisualBasic.dll derlemelerine her zaman başvurulur.  
  
 Her Vbc.exe derlemesinde bulunması gereken ek derleyici seçeneklerini belirtmek için Vbc. rsp dosyasını değiştirebilirsiniz (seçenek belirtildiğinde hariç `-noconfig` ). Daha fazla bilgi için bkz. [@ (yanıt dosyası belirtme)](specify-response-file.md).  
  
 Derleyici, son komuta geçirilen seçenekleri işler `vbc` . Bu nedenle, komut satırındaki herhangi bir seçenek, vbc. rsp dosyasında aynı seçeneğin ayarını geçersiz kılar.  
  
> [!NOTE]
> `-noconfig`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-nostdlib (Visual Basic)](nostdlib.md)
- [Visual Basic Command-Line derleyicisi](index.md)
- [@ (Yanıt Dosyasını Belirtin)](specify-response-file.md)
- [-başvuru (Visual Basic)](reference.md)
