---
title: İki Kez Arabelleğe Almayı Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: 5b22336221c7bdda3c9dd7adf23308a2b0bad450
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169916"
---
# <a name="using-double-buffering"></a><span data-ttu-id="ec9b3-102">İki Kez Arabelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="ec9b3-102">Using Double Buffering</span></span>
<span data-ttu-id="ec9b3-103">İki kez arabelleğe alınan grafikler, karmaşık boyama işlemler içeren, uygulamalarınızda titreşimi azaltmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec9b3-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="ec9b3-104">.NET Framework iki kez arabelleğe alma için yerleşik destek içerir veya yönetebilir ve grafikleri elle işleme.</span><span class="sxs-lookup"><span data-stu-id="ec9b3-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec9b3-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ec9b3-105">In This Section</span></span>  
 [<span data-ttu-id="ec9b3-106">İki Kez Arabelleğe Alınan Grafikler</span><span class="sxs-lookup"><span data-stu-id="ec9b3-106">Double Buffered Graphics</span></span>](double-buffered-graphics.md)  
 <span data-ttu-id="ec9b3-107">Çift arabelleğe alma kavram ve ana hatlarını .NET Framework Destek sunuyor.</span><span class="sxs-lookup"><span data-stu-id="ec9b3-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="ec9b3-108">Nasıl yapılır: Formlar ve denetimler için çift arabelleğe alma ile grafik titreşimini azaltma</span><span class="sxs-lookup"><span data-stu-id="ec9b3-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="ec9b3-109">Varsayılan .NET Framework Destek arabelleğe çift nasıl yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="ec9b3-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="ec9b3-110">Nasıl yapılır: Arabelleğe alınan grafikleri elle yönetme</span><span class="sxs-lookup"><span data-stu-id="ec9b3-110">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="ec9b3-111">Uygulamalarda iki kez arabelleğe alma yönetme işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ec9b3-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="ec9b3-112">Nasıl yapılır: Arabelleğe alınan grafikleri elle işleme</span><span class="sxs-lookup"><span data-stu-id="ec9b3-112">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="ec9b3-113">İki kez arabelleğe alınan grafikler nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec9b3-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ec9b3-114">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ec9b3-114">Reference</span></span>  
 <span data-ttu-id="ec9b3-115"><xref:System.Windows.Forms.Control.SetStyle%2A> Denetim yöntemi iki kez arabelleğe almayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec9b3-115"><xref:System.Windows.Forms.Control.SetStyle%2A> Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="ec9b3-116"><xref:System.Drawing.BufferedGraphicsContext> Grafik arabellekleri oluşturmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec9b3-116"><xref:System.Drawing.BufferedGraphicsContext> Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="ec9b3-117">Bir uygulama etki alanı için arabelleğe alınan grafikleri bağlam erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec9b3-117">Provides access to the buffered graphics context for a application domain.</span></span>
