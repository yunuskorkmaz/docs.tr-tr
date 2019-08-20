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
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="01606-102">-preferreduilang (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="01606-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="01606-103">`-preferreduilang` Derleyici seçeneğini kullanarak, C# derleyicinin hata iletileri gibi çıktıyı görüntülediği dili belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01606-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01606-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01606-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="01606-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="01606-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="01606-106">Derleyici çıktısı için kullanılacak dilin [dil adı](/windows/desktop/Intl/language-names) .</span><span class="sxs-lookup"><span data-stu-id="01606-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01606-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01606-107">Remarks</span></span>  
 <span data-ttu-id="01606-108">Derleyicinin hata iletileri ve `-preferreduilang` diğer komut satırı çıktıları için kullanmasını istediğiniz dili C# belirtmek için derleyici seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01606-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="01606-109">Dile ait dil paketi yüklü değilse, bunun yerine işletim sisteminin dil ayarı kullanılır ve hiçbir hata bildirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="01606-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="01606-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01606-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01606-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01606-111">See also</span></span>

- [<span data-ttu-id="01606-112">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="01606-112">C# Compiler Options</span></span>](./index.md)
