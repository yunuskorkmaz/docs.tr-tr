---
title: -preferreduilang (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 7ebafcf446c9033c93e0c5fa5e11ea2930bd2e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602563"
---
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (C# Derleyici Seçenekleri)
`-preferreduilang` Derleyici seçeneğini kullanarak, C# derleyicisinin hata iletileri gibi çıktıyı görüntülediği dili belirtebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `language`  
 Derleyici çıktısı için kullanılacak dilin [dil adı.](/windows/desktop/Intl/language-names)  
  
## <a name="remarks"></a>Açıklamalar  
 `-preferreduilang` C# derleyicisinin hata iletileri ve diğer komut satırı çıktısı için kullanmasını istediğiniz dili belirtmek için derleyici seçeneğini kullanabilirsiniz. Dil için dil paketi yüklenmezse, bunun yerine işletim sisteminin dil ayarı kullanılır ve hata bildirilir.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Gereksinimler  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
