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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662549"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="813a1-102">-preferreduilang (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="813a1-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="813a1-103">Kullanarak `-preferreduilang` derleyici seçeneği, C# derleyicisi hata iletileri gibi bir çıkış görüntüler dil belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="813a1-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="813a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="813a1-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="813a1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="813a1-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="813a1-106">[Dil adı](/windows/desktop/Intl/language-names) Derleyici çıktısı için kullanılacak dili.</span><span class="sxs-lookup"><span data-stu-id="813a1-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="813a1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="813a1-107">Remarks</span></span>  
 <span data-ttu-id="813a1-108">Kullanabileceğiniz `-preferreduilang` hata iletileri ve diğer komut satırı çıktısı için kullanılacak C# Derleyici istediğiniz dilini belirtmek için derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="813a1-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="813a1-109">Dile ait dil paketini yüklü değilse, işletim sisteminin dil ayarından yerine kullanılır ve herhangi bir hata bildirilir.</span><span class="sxs-lookup"><span data-stu-id="813a1-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="813a1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="813a1-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="813a1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="813a1-111">See also</span></span>

- [<span data-ttu-id="813a1-112">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="813a1-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
