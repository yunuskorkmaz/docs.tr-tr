---
title: "StatusStrip Denetimine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5f06d155972846b3c04a60d448b300d8cdc5d1c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="statusstrip-control-overview"></a><span data-ttu-id="77e08-102">StatusStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="77e08-102">StatusStrip Control Overview</span></span>
<span data-ttu-id="77e08-103">A <xref:System.Windows.Forms.StatusStrip> denetim üzerinde görüntülenen bir nesne hakkındaki bilgileri görüntüler bir <xref:System.Windows.Forms.Form>, nesnenin bileşenleri veya o nesnenin işlemi, uygulamanızda ilgili bağlamsal bilgi.</span><span class="sxs-lookup"><span data-stu-id="77e08-103">A <xref:System.Windows.Forms.StatusStrip> control displays information about an object being viewed on a <xref:System.Windows.Forms.Form>, the object's components, or contextual information that relates to that object's operation within your application.</span></span> <span data-ttu-id="77e08-104">Genellikle, bir <xref:System.Windows.Forms.StatusStrip> denetim oluşur <xref:System.Windows.Forms.ToolStripStatusLabel> nesneleri, metin, simge ya da her ikisini de her biri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="77e08-104">Typically, a <xref:System.Windows.Forms.StatusStrip> control consists of <xref:System.Windows.Forms.ToolStripStatusLabel> objects, each of which displays text, an icon, or both.</span></span> <span data-ttu-id="77e08-105"><xref:System.Windows.Forms.StatusStrip> De içerebilir <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, ve <xref:System.Windows.Forms.ToolStripProgressBar> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="77e08-105">The <xref:System.Windows.Forms.StatusStrip> can also contain <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, and <xref:System.Windows.Forms.ToolStripProgressBar> controls.</span></span>  
  
 <span data-ttu-id="77e08-106">Varsayılan <xref:System.Windows.Forms.StatusStrip> hiçbir paneller vardır.</span><span class="sxs-lookup"><span data-stu-id="77e08-106">The default <xref:System.Windows.Forms.StatusStrip> has no panels.</span></span> <span data-ttu-id="77e08-107">Bölmeleri eklemek için bir <xref:System.Windows.Forms.StatusStrip>, kullanın <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77e08-107">To add panels to a <xref:System.Windows.Forms.StatusStrip>, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="77e08-108">İşleme için kapsamlı destek <xref:System.Windows.Forms.StatusStrip> öğeleri ve Visual Studio yaygın komutları.</span><span class="sxs-lookup"><span data-stu-id="77e08-108">There is extensive support for handling <xref:System.Windows.Forms.StatusStrip> items and common commands in Visual Studio.</span></span>  
  
 <span data-ttu-id="77e08-109">Ayrıca bkz. [StatusStrip öğeleri koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="77e08-109">Also see [StatusStrip Items Collection Editor](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip Tasks Dialog Box](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="77e08-110">Ancak <xref:System.Windows.Forms.StatusStrip> değiştirir ve genişletir <xref:System.Windows.Forms.StatusBar> önceki sürümlerinde, denetimin <xref:System.Windows.Forms.StatusBar> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="77e08-110">Although <xref:System.Windows.Forms.StatusStrip> replaces and extends the <xref:System.Windows.Forms.StatusBar> control of previous versions, <xref:System.Windows.Forms.StatusBar> is retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="important-statusstrip-members"></a><span data-ttu-id="77e08-111">Önemli StatusStrip üyeleri</span><span class="sxs-lookup"><span data-stu-id="77e08-111">Important StatusStrip Members</span></span>  
  
|<span data-ttu-id="77e08-112">Ad</span><span class="sxs-lookup"><span data-stu-id="77e08-112">Name</span></span>|<span data-ttu-id="77e08-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77e08-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|<span data-ttu-id="77e08-114">Belirten değeri alır veya ayarlar olup olmadığını <xref:System.Windows.Forms.StatusStrip> taşması işlevselliği destekler.</span><span class="sxs-lookup"><span data-stu-id="77e08-114">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|<span data-ttu-id="77e08-115">Belirten değeri alır veya ayarlar olup olmadığını <xref:System.Windows.Forms.StatusStrip> uzatır uçtan uca içinde kendi <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="77e08-115">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> stretches from end to end in its <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
  
### <a name="important-statusstrip-companion-classes"></a><span data-ttu-id="77e08-116">Önemli StatusStrip yardımcı sınıfları</span><span class="sxs-lookup"><span data-stu-id="77e08-116">Important StatusStrip Companion Classes</span></span>  
  
|<span data-ttu-id="77e08-117">Ad</span><span class="sxs-lookup"><span data-stu-id="77e08-117">Name</span></span>|<span data-ttu-id="77e08-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77e08-118">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|<span data-ttu-id="77e08-119">Masası'nda temsil eden bir <xref:System.Windows.Forms.StatusStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="77e08-119">Represents a panel in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|<span data-ttu-id="77e08-120">İlişkili bir görüntüler <xref:System.Windows.Forms.ToolStripDropDown> alınacağı kullanıcı tek bir öğe seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77e08-120">Displays an associated <xref:System.Windows.Forms.ToolStripDropDown> from which the user can select a single item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|<span data-ttu-id="77e08-121">Standart bir düğme ve bir açılır menü iki parçalı bir denetimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="77e08-121">Represents a two-part control that is a standard button and a drop-down menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|<span data-ttu-id="77e08-122">Bir işleminin tamamlanma durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="77e08-122">Displays the completion state of a process.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77e08-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77e08-123">See Also</span></span>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
