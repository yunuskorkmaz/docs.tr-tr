---
title: -utf8output (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /utf8output
helpviewer_keywords:
- utf8output compiler option [C#]
- /utf8output compiler option [C#]
- -utf8output compiler option [C#]
ms.assetid: 27ff7381-c281-45d7-b2eb-1ad644b1354e
ms.openlocfilehash: abed8247569cd5885e6241be141271bf75bfa2be
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606307"
---
# <a name="-utf8output-c-compiler-options"></a><span data-ttu-id="1c93b-102">-utf8output (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1c93b-102">-utf8output (C# Compiler Options)</span></span>
<span data-ttu-id="1c93b-103">**-Utf8output** seçeneği, DERLEYICI çıkışını utf-8 kodlaması kullanarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1c93b-103">The **-utf8output** option displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c93b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c93b-104">Syntax</span></span>  
  
```console  
-utf8output  
```  
  
## <a name="remarks"></a><span data-ttu-id="1c93b-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c93b-105">Remarks</span></span>  
 <span data-ttu-id="1c93b-106">Bazı uluslararası yapılandırmalarda, Derleyici çıktısı konsolunda doğru şekilde görüntülenemez.</span><span class="sxs-lookup"><span data-stu-id="1c93b-106">In some international configurations, compiler output cannot correctly be displayed in the console.</span></span> <span data-ttu-id="1c93b-107">Bu yapılandırmalarda **-utf8output** ve derleyici çıkışını bir dosyaya yeniden yönlendir ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c93b-107">In these configurations, use **-utf8output** and redirect compiler output to a file.</span></span>  
  
 <span data-ttu-id="1c93b-108">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="1c93b-108">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c93b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c93b-109">See also</span></span>

- [<span data-ttu-id="1c93b-110">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="1c93b-110">C# Compiler Options</span></span>](./index.md)
