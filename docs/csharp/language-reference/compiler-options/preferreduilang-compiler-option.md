---
description: -preferreduilang (C# derleyici seçenekleri)
title: -preferreduilang (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: f68652e910651ab5c4184376d9eb7729303382d9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124857"
---
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (C# derleyici seçenekleri)
`-preferreduilang`Derleyici seçeneğini kullanarak, C# derleyicisinin hata iletileri gibi çıktıyı görüntülediği dili belirtebilirsiniz.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 `language`  
 Derleyici çıktısı için kullanılacak dilin [dil adı](/windows/desktop/Intl/language-names) .  
  
## <a name="remarks"></a>Açıklamalar  
 `-preferreduilang`C# derleyicisinin hata iletileri ve diğer komut satırı çıktıları için kullanmasını istediğiniz dili belirtmek için derleyici seçeneğini kullanabilirsiniz. Dile ait dil paketi yüklü değilse, bunun yerine işletim sisteminin dil ayarı kullanılır ve hiçbir hata bildirilmemiştir.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Gereksinimler  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
