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
ms.openlocfilehash: d079441e91ff90bcc974564bbd7069e0548a7d77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575303"
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
