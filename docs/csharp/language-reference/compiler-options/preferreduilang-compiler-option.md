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
ms.openlocfilehash: 490f5926fb50cfdae740b7749d72ea6c9a1f8cc9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193822"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="44fa3-103">-preferreduilang (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="44fa3-103">-preferreduilang (C# Compiler Options)</span></span>

<span data-ttu-id="44fa3-104">`-preferreduilang`Derleyici seçeneğini kullanarak, C# derleyicisinin hata iletileri gibi çıktıyı görüntülediği dili belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44fa3-104">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44fa3-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="44fa3-105">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="44fa3-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="44fa3-106">Arguments</span></span>  

 `language`  
 <span data-ttu-id="44fa3-107">Derleyici çıktısı için kullanılacak dilin [dil adı](/windows/desktop/Intl/language-names) .</span><span class="sxs-lookup"><span data-stu-id="44fa3-107">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44fa3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44fa3-108">Remarks</span></span>  

 <span data-ttu-id="44fa3-109">`-preferreduilang`C# derleyicisinin hata iletileri ve diğer komut satırı çıktıları için kullanmasını istediğiniz dili belirtmek için derleyici seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44fa3-109">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="44fa3-110">Dile ait dil paketi yüklü değilse, bunun yerine işletim sisteminin dil ayarı kullanılır ve hiçbir hata bildirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="44fa3-110">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="44fa3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44fa3-111">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44fa3-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44fa3-112">See also</span></span>

- [<span data-ttu-id="44fa3-113">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="44fa3-113">C# Compiler Options</span></span>](./index.md)
