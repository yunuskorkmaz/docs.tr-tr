---
title: Uygulama Formlarına Erişme
ms.date: 07/20/2015
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
ms.openlocfilehash: 44f98632fd2fd6c4c087a78b805d5b7da750df87
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410211"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="3f71b-102">Uygulama Formlarına Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f71b-102">Accessing Application Forms (Visual Basic)</span></span>

<span data-ttu-id="3f71b-103">`My.Forms`Nesnesi, uygulamanın projesinde belirtilen her bir Windows formunun örneğine erişmenin kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f71b-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="3f71b-104">`My.Application`Uygulamanın giriş ekranına ve ana forma erişmek ve uygulamanın açık formlarının bir listesini almak için nesnenin özelliklerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f71b-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="3f71b-105">Görevler</span><span class="sxs-lookup"><span data-stu-id="3f71b-105">Tasks</span></span>  

 <span data-ttu-id="3f71b-106">Aşağıdaki tabloda, bir uygulamanın formlarına nasıl erişileceğini gösteren örnekler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3f71b-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="3f71b-107">Alıcı</span><span class="sxs-lookup"><span data-stu-id="3f71b-107">To</span></span>|<span data-ttu-id="3f71b-108">Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f71b-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="3f71b-109">Bir uygulamadaki başka bir formdan bir forma erişin.</span><span class="sxs-lookup"><span data-stu-id="3f71b-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="3f71b-110">My.Forms Nesnesi</span><span class="sxs-lookup"><span data-stu-id="3f71b-110">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="3f71b-111">Tüm uygulamanın açık formlarının unvanlarını görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="3f71b-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="3f71b-112">Uygulama başladıktan sonra giriş ekranını durum bilgileriyle güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="3f71b-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="3f71b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f71b-113">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>
- [<span data-ttu-id="3f71b-114">My.Forms Nesnesi</span><span class="sxs-lookup"><span data-stu-id="3f71b-114">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
