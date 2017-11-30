---
title: "-preferreduilang (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ccf25e9a5d5d025f9024519b41c4afa17a5081f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="preferreduilang-c-compiler-options"></a>/preferreduilang (C# Derleyici Seçenekleri)
Kullanarak `/preferreduilang` derleyici seçeneği, C# Derleyici hata iletileri gibi bir çıkış görüntüler dil belirtebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/preferreduilang: language  
```  
  
## <a name="arguments"></a>Arguments  
 `language`  
 [Dil adı](http://go.microsoft.com/fwlink/p/?LinkId=236992) derleyici çıktı için kullanılacak dili.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `/preferreduilang` derleyici seçeneği hata iletileri ve diğer komut satırı çıktısı için kullanmak için C# Derleyici istediğiniz dili belirtin. Dili için dil paketi yüklü değilse, işletim sisteminin dil ayarından yerine kullanılır ve herhangi bir hata bildirdi.  
  
```csharp  
csc.exe /preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Gereksinimler  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
