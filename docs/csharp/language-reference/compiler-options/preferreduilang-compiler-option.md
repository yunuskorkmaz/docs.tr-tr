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
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="207f7-102">-preferreduilang (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="207f7-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="207f7-103">Kullanarak `-preferreduilang` derleyici seçeneği, C# derleyicisi hata iletileri gibi bir çıkış görüntüler dil belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="207f7-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="207f7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="207f7-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="207f7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="207f7-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="207f7-106">[Dil adı](/windows/desktop/Intl/language-names) Derleyici çıktısı için kullanılacak dili.</span><span class="sxs-lookup"><span data-stu-id="207f7-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="207f7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="207f7-107">Remarks</span></span>  
 <span data-ttu-id="207f7-108">Kullanabileceğiniz `-preferreduilang` hata iletileri ve diğer komut satırı çıktısı için kullanılacak C# Derleyici istediğiniz dilini belirtmek için derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="207f7-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="207f7-109">Dile ait dil paketini yüklü değilse, işletim sisteminin dil ayarından yerine kullanılır ve herhangi bir hata bildirilir.</span><span class="sxs-lookup"><span data-stu-id="207f7-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="207f7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="207f7-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="207f7-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="207f7-111">See Also</span></span>

- [<span data-ttu-id="207f7-112">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="207f7-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
