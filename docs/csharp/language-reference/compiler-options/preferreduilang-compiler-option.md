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
ms.openlocfilehash: 4fcf075dd951d733d294a62de98365c77b16a51d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="e45a1-102">-preferreduilang (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e45a1-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="e45a1-103">Kullanarak `-preferreduilang` derleyici seçeneği, C# Derleyici hata iletileri gibi bir çıkış görüntüler dil belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e45a1-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e45a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e45a1-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="e45a1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e45a1-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="e45a1-106">[Dil adı](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) derleyici çıktı için kullanılacak dili.</span><span class="sxs-lookup"><span data-stu-id="e45a1-106">The [language name](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e45a1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e45a1-107">Remarks</span></span>  
 <span data-ttu-id="e45a1-108">Kullanabileceğiniz `-preferreduilang` derleyici seçeneği hata iletileri ve diğer komut satırı çıktısı için kullanmak için C# Derleyici istediğiniz dili belirtin.</span><span class="sxs-lookup"><span data-stu-id="e45a1-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="e45a1-109">Dili için dil paketi yüklü değilse, işletim sisteminin dil ayarından yerine kullanılır ve herhangi bir hata bildirdi.</span><span class="sxs-lookup"><span data-stu-id="e45a1-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="e45a1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e45a1-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e45a1-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e45a1-111">See Also</span></span>  
 [<span data-ttu-id="e45a1-112">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e45a1-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
