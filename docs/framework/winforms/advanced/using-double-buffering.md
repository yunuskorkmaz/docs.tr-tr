---
title: "İki Kez Arabelleğe Almayı Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5ad51e27c3d31ece1d11831c953023bedba3a97
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="using-double-buffering"></a><span data-ttu-id="32a3a-102">İki Kez Arabelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="32a3a-102">Using Double Buffering</span></span>
<span data-ttu-id="32a3a-103">Karmaşık Boyama işlemleri içeren uygulamalarınızı titreşimi azaltmak için iki kez arabelleğe alınan grafikler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32a3a-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="32a3a-104">.NET Framework çift arabelleğe alma için yerleşik destek içerir veya yönetebilir ve grafikleri elle işleme.</span><span class="sxs-lookup"><span data-stu-id="32a3a-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="32a3a-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="32a3a-105">In This Section</span></span>  
 [<span data-ttu-id="32a3a-106">Çift arabelleğe alınan grafikleri</span><span class="sxs-lookup"><span data-stu-id="32a3a-106">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 <span data-ttu-id="32a3a-107">Çift arabelleğe alma kavram ve anahatları .NET Framework destek sunar.</span><span class="sxs-lookup"><span data-stu-id="32a3a-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="32a3a-108">Nasıl yapılır: formlar ve denetimler için çift arabelleğe alma ile grafik titreşimini azaltma</span><span class="sxs-lookup"><span data-stu-id="32a3a-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="32a3a-109">Varsayılan .NET Framework Destek arabelleğe çift kullanımı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="32a3a-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="32a3a-110">Nasıl yapılır: arabelleğe alınan grafikleri elle yönetme</span><span class="sxs-lookup"><span data-stu-id="32a3a-110">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="32a3a-111">Uygulamalarda iki kez arabelleğe alma yönetmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="32a3a-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="32a3a-112">Nasıl yapılır: arabelleğe alınan grafikleri elle işleme</span><span class="sxs-lookup"><span data-stu-id="32a3a-112">How to: Manually Render Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="32a3a-113">İki kez arabelleğe alınan grafikler işlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="32a3a-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="32a3a-114">Başvuru</span><span class="sxs-lookup"><span data-stu-id="32a3a-114">Reference</span></span>  
 <span data-ttu-id="32a3a-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span><span class="sxs-lookup"><span data-stu-id="32a3a-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span></span>  
 <span data-ttu-id="32a3a-116">İki kez arabelleğe alma sağlayan denetim yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32a3a-116">Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="32a3a-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span><span class="sxs-lookup"><span data-stu-id="32a3a-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span></span>  
 <span data-ttu-id="32a3a-118">Grafik arabellekleri oluşturmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="32a3a-118">Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="32a3a-119">Uygulama etki alanı için arabelleğe alınan grafikleri bağlam erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="32a3a-119">Provides access to the buffered graphics context for a application domain.</span></span>
