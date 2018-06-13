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
ms.openlocfilehash: 21a3baceb8a46723de1c633e415af0660bb41840
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211757"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="4e3a1-102">-preferreduilang (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4e3a1-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="4e3a1-103">Kullanarak `-preferreduilang` derleyici seçeneği, C# Derleyici hata iletileri gibi bir çıkış görüntüler dil belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e3a1-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e3a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e3a1-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="4e3a1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4e3a1-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="4e3a1-106">[Dil adı](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) derleyici çıktı için kullanılacak dili.</span><span class="sxs-lookup"><span data-stu-id="4e3a1-106">The [language name](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e3a1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e3a1-107">Remarks</span></span>  
 <span data-ttu-id="4e3a1-108">Kullanabileceğiniz `-preferreduilang` derleyici seçeneği hata iletileri ve diğer komut satırı çıktısı için kullanmak için C# Derleyici istediğiniz dili belirtin.</span><span class="sxs-lookup"><span data-stu-id="4e3a1-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="4e3a1-109">Dili için dil paketi yüklü değilse, işletim sisteminin dil ayarından yerine kullanılır ve herhangi bir hata bildirdi.</span><span class="sxs-lookup"><span data-stu-id="4e3a1-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="4e3a1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e3a1-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e3a1-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4e3a1-111">See Also</span></span>  
 [<span data-ttu-id="4e3a1-112">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4e3a1-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
