---
title: Proje .NET Framework 3.0 ve 3.5 Visual Studio 2010 hedefleme yazma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 95348ad57bb4dce1799c1ddf741b69f0e2b969af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a><span data-ttu-id="f093d-102">Proje .NET Framework 3.0 ve 3.5 Visual Studio 2010 hedefleme yazma</span><span class="sxs-lookup"><span data-stu-id="f093d-102">Writing Projects Targeting the .NET Framework 3.0 and 3.5 in Visual Studio 2010</span></span>
<span data-ttu-id="f093d-103">Kullanabileceğiniz [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] hedefleyen projeler oluşturmak için [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sürüm 3.0 veya 3.5.</span><span class="sxs-lookup"><span data-stu-id="f093d-103">You can use [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] to create projects that target the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version 3.0 or 3.5.</span></span> <span data-ttu-id="f093d-104">Bu konu bunun nasıl yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f093d-104">This topic describes how to do this.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f093d-105">Etkinlikler eklerken emin olun istenen sürümüyle [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f093d-105">When adding activities, make sure that the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] is set.</span></span> <span data-ttu-id="f093d-106">İş akışı hedef sürümü etkinlikleri eklendikten sonra değiştirilmesi başarısız doğrulama da iş akışı neden olur.</span><span class="sxs-lookup"><span data-stu-id="f093d-106">Changing the target version of the workflow after activities are added will cause the workflow to fail validation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f093d-107">Var olan iş akışlarında açma [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] sahip olan .net Framework 3.5 etkinlikleri sırasında bir hata neden olacak `this.SetValue()`.</span><span class="sxs-lookup"><span data-stu-id="f093d-107">Opening existing workflows in [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] that have .Net Framework 3.5 activities will cause an error at `this.SetValue()`.</span></span> <span data-ttu-id="f093d-108">.Net önceki sürümleriyle oluşturulan projeleri açabilmek Framework, önce boş bir iş akışı Tasarımcısı'nda açın ve bir .net ekleyin Framework 3.5 etkinlik.</span><span class="sxs-lookup"><span data-stu-id="f093d-108">In order to open projects created with previous versions of the .Net Framework, first open a blank workflow in the designer and add a .Net Framework 3.5 activity.</span></span>  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a><span data-ttu-id="f093d-109">Visual Studio 2010 ile .NET Framework 3.0 veya 3.5 proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f093d-109">To create a .NET Framework  3.0 or 3.5 project with Visual Studio 2010</span></span>  
  
1.  <span data-ttu-id="f093d-110">Açık [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f093d-110">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="f093d-111">Seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="f093d-111">Select **File**, **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="f093d-112">İletişim kutusunun üstündeki aşağı açılan listesinde, istediğiniz sürümü seçin [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f093d-112">In the drop-down list at the top of the dialog box, select the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a><span data-ttu-id="f093d-113">.NET Framework'ün hedeflenen sürümüne yükseltmek için</span><span class="sxs-lookup"><span data-stu-id="f093d-113">To upgrade the targeted version of the .NET Framework</span></span>  
  
1.  <span data-ttu-id="f093d-114">Çözüm Gezgini'nde projeye sağ tıklayın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="f093d-114">Right-click the project in Solution Explorer, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="f093d-115">İçinde **hedef Framework** aşağı açılan listesinde, istediğiniz sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="f093d-115">In the **Target Framework** drop-down list, select the desired version.</span></span>
