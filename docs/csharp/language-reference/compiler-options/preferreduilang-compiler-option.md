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
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="d6625-102">-preferreduilang (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="d6625-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="d6625-103">`-preferreduilang` Derleyici seçeneğini kullanarak, C# derleyicisinin hata iletileri gibi çıktıyı görüntülediği dili belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6625-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6625-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6625-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="d6625-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="d6625-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="d6625-106">Derleyici çıktısı için kullanılacak dilin [dil adı.](/windows/desktop/Intl/language-names)</span><span class="sxs-lookup"><span data-stu-id="d6625-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6625-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6625-107">Remarks</span></span>  
 <span data-ttu-id="d6625-108">`-preferreduilang` C# derleyicisinin hata iletileri ve diğer komut satırı çıktısı için kullanmasını istediğiniz dili belirtmek için derleyici seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6625-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="d6625-109">Dil için dil paketi yüklenmezse, bunun yerine işletim sisteminin dil ayarı kullanılır ve hata bildirilir.</span><span class="sxs-lookup"><span data-stu-id="d6625-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="d6625-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6625-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6625-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6625-111">See also</span></span>

- [<span data-ttu-id="d6625-112">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d6625-112">C# Compiler Options</span></span>](./index.md)
