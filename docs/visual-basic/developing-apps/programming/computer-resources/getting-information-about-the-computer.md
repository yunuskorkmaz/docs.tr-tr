---
description: 'Hakkında daha fazla bilgi edinin: bilgisayar hakkında bilgi alma (Visual Basic)'
title: Bilgisayar Hakkında Bilgi Alma
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Info object [Visual Basic], tasks
ms.assetid: 13c145bc-5c85-4fea-a5dd-2ca8681a0252
ms.openlocfilehash: 11198082950fcfd648b5ba8fa859b8765e3f628c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797776"
---
# <a name="getting-information-about-the-computer-visual-basic"></a><span data-ttu-id="3c793-103">Bilgisayar Hakkında Bilgi Alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c793-103">Getting Information about the Computer (Visual Basic)</span></span>

<span data-ttu-id="3c793-104">`My.Computer.Info`Nesnesi, bilgisayarın belleği, yüklü derlemeler, ad ve işletim sistemi hakkında bilgi almak için özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c793-104">The `My.Computer.Info` object provides properties for getting information about the computer's memory, loaded assemblies, name, and operating system.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c793-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c793-105">Remarks</span></span>

<span data-ttu-id="3c793-106">Bu tablo, genellikle nesnesi aracılığıyla gerçekleştirilen görevleri listeler `My.Computer.Info` ve bunların her birinin nasıl gerçekleştirileceğini gösteren konuların noktalarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c793-106">This table lists tasks commonly accomplished through the `My.Computer.Info` object and points to topics demonstrating how to perform each.</span></span>

|<span data-ttu-id="3c793-107">Amaç</span><span class="sxs-lookup"><span data-stu-id="3c793-107">To</span></span>|<span data-ttu-id="3c793-108">Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c793-108">See</span></span>|
|---|---|
|<span data-ttu-id="3c793-109">Uygulamanın yüklendiği bilgisayar için ne kadar kullanılabilir sanal adres alanı olduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="3c793-109">Determine how much virtual address space is available for the computer on which the application is installed</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.TotalVirtualMemory%2A>|
|<span data-ttu-id="3c793-110">Uygulamanın çalıştığı bilgisayarın Platform türünü belirleme</span><span class="sxs-lookup"><span data-stu-id="3c793-110">Determine the platform type of the computer on which the application is running</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSPlatform%2A>|
|<span data-ttu-id="3c793-111">Uygulamanın çalıştığı bilgisayarın işletim sistemini belirleme</span><span class="sxs-lookup"><span data-stu-id="3c793-111">Determine the operating system of the computer on which the application is running</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName%2A>|
|<span data-ttu-id="3c793-112">Uygulamanın üzerinde çalıştığı bilgisayarda hangi hizmet paketlerinin yüklü olduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="3c793-112">Determine what service packs have been installed on the computer on which the application is running</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSVersion%2A>|
|<span data-ttu-id="3c793-113">`UICulture`Uygulamanın üzerinde çalıştığı bilgisayarda yüklü ' yı belirleme.</span><span class="sxs-lookup"><span data-stu-id="3c793-113">Determine the installed `UICulture` on the computer on which the application is running.</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.InstalledUICulture%2A>|

## <a name="see-also"></a><span data-ttu-id="3c793-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c793-114">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
