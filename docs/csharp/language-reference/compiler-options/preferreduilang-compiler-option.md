---
title: -preferreduilang (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 7ebafcf446c9033c93e0c5fa5e11ea2930bd2e1e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602563"
---
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (C# derleyici seçenekleri)
`-preferreduilang` Derleyici seçeneğini kullanarak, C# derleyicinin hata iletileri gibi çıktıyı görüntülediği dili belirtebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Arguments  
 `language`  
 Derleyici çıktısı için kullanılacak dilin [dil adı](/windows/desktop/Intl/language-names) .  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyicinin hata iletileri ve `-preferreduilang` diğer komut satırı çıktıları için kullanmasını istediğiniz dili C# belirtmek için derleyici seçeneğini kullanabilirsiniz. Dile ait dil paketi yüklü değilse, bunun yerine işletim sisteminin dil ayarı kullanılır ve hiçbir hata bildirilmemiştir.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Gereksinimler  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
