---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: ee7cd1b8039a8d9312a8b058cc85c41ca536ed2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401946"
---
# <a name="-noconfig"></a>-noconfig
Derleyicinin yaygın olarak kullanılan .NET Framework derlemelerine otomatik olarak başvurmamalıdır veya `System` ve ad alanlarını içeri aktaramamalıdır `Microsoft.VisualBasic` .  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `-noconfig`Seçeneği, derleyicinin Vbc. exe dosyası ile aynı dizinde bulunan Vbc. rsp dosyası ile derlenmeyeceğini söyler. Vbc. rsp dosyası, yaygın olarak kullanılan .NET Framework derlemelerine başvurur ve `System` ve `Microsoft.VisualBasic` ad alanlarını içeri aktarır. Seçenek belirtilmediği takdirde derleyici System. dll derlemesine dolaylı olarak başvurur `-nostdlib` . `-nostdlib`Seçeneği, derleyicinin Vbc. rsp ile derlenmeyeceğini veya System. dll derlemesine otomatik olarak başvurmayacağını söyler.  
  
> [!NOTE]
> Mscorlib. dll ve Microsoft. VisualBasic. dll derlemelerine her zaman başvurulur.  
  
 Vbc. rsp dosyasını, her Vbc. exe derlemesine dahil edilecek ek derleyici seçeneklerini belirtmek için değiştirebilirsiniz (seçeneğini belirtirken hariç `-noconfig` ). Daha fazla bilgi için bkz. [@ (yanıt dosyası belirtme)](specify-response-file.md).  
  
 Derleyici, son komuta geçirilen seçenekleri işler `vbc` . Bu nedenle, komut satırındaki herhangi bir seçenek, vbc. rsp dosyasında aynı seçeneğin ayarını geçersiz kılar.  
  
> [!NOTE]
> `-noconfig`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-nostdlib (Visual Basic)](nostdlib.md)
- [Visual Basic komut satırı derleyicisi](index.md)
- [@ (Yanıt Dosyasını Belirtin)](specify-response-file.md)
- [-başvuru (Visual Basic)](reference.md)
