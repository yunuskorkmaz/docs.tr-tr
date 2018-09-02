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
ms.openlocfilehash: a1fbbb8415e5e3405f039489aa071b0624065a9d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405897"
---
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (C# Derleyici Seçenekleri)
Kullanarak `-preferreduilang` derleyici seçeneği, C# derleyicisi hata iletileri gibi bir çıkış görüntüler dil belirtebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Arguments  
 `language`  
 [Dil adı](/windows/desktop/Intl/language-names) Derleyici çıktısı için kullanılacak dili.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `-preferreduilang` hata iletileri ve diğer komut satırı çıktısı için kullanılacak C# Derleyici istediğiniz dilini belirtmek için derleyici seçeneği. Dile ait dil paketini yüklü değilse, işletim sisteminin dil ayarından yerine kullanılır ve herhangi bir hata bildirilir.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Gereksinimler  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
