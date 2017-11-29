---
title: "Çok fazla sayıda DLL uygulama istemci"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b9278134e937ac8bf4626237954432d727ac0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="e66c7-102">Çok fazla sayıda DLL uygulama istemci</span><span class="sxs-lookup"><span data-stu-id="e66c7-102">Too many DLL application clients</span></span>
<span data-ttu-id="e66c7-103">Dinamik bağlantı kitaplığının (DLL) [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] yalnızca sınırlı sayıda konak uygulamalar tarafından erişim barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="e66c7-103">The dynamic-link library (DLL) for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="e66c7-104">Uygulamanız ve diğer uygulamalar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] (bazıları erişilebilir, uygulamanız tarafından) konakları tüm erişmeye çalıştığınız [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] aynı anda DLL.</span><span class="sxs-lookup"><span data-stu-id="e66c7-104">Your application and other applications that are [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] hosts (some of which may be accessed by your application) are all attempting to access the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e66c7-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e66c7-105">To correct this error</span></span>  
  
-   <span data-ttu-id="e66c7-106">Açık uygulamaları erişme sayısını azaltın [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e66c7-106">Reduce the number of open applications accessing [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e66c7-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e66c7-107">See Also</span></span>  
 [<span data-ttu-id="e66c7-108">Hata türleri</span><span class="sxs-lookup"><span data-stu-id="e66c7-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
