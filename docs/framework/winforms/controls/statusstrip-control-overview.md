---
title: StatusStrip Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
ms.openlocfilehash: b915be2db6865a95d2d37afda58983dbb2edca27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537914"
---
# <a name="statusstrip-control-overview"></a><span data-ttu-id="5098b-102">StatusStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5098b-102">StatusStrip Control Overview</span></span>
<span data-ttu-id="5098b-103">A <xref:System.Windows.Forms.StatusStrip> denetim üzerinde görüntülenen bir nesne hakkındaki bilgileri görüntüler bir <xref:System.Windows.Forms.Form>, nesnenin bileşenleri veya o nesnenin işlemi, uygulamanızda ilgili bağlamsal bilgi.</span><span class="sxs-lookup"><span data-stu-id="5098b-103">A <xref:System.Windows.Forms.StatusStrip> control displays information about an object being viewed on a <xref:System.Windows.Forms.Form>, the object's components, or contextual information that relates to that object's operation within your application.</span></span> <span data-ttu-id="5098b-104">Genellikle, bir <xref:System.Windows.Forms.StatusStrip> denetim oluşur <xref:System.Windows.Forms.ToolStripStatusLabel> nesneleri, metin, simge ya da her ikisini de her biri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5098b-104">Typically, a <xref:System.Windows.Forms.StatusStrip> control consists of <xref:System.Windows.Forms.ToolStripStatusLabel> objects, each of which displays text, an icon, or both.</span></span> <span data-ttu-id="5098b-105"><xref:System.Windows.Forms.StatusStrip> De içerebilir <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, ve <xref:System.Windows.Forms.ToolStripProgressBar> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="5098b-105">The <xref:System.Windows.Forms.StatusStrip> can also contain <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, and <xref:System.Windows.Forms.ToolStripProgressBar> controls.</span></span>  
  
 <span data-ttu-id="5098b-106">Varsayılan <xref:System.Windows.Forms.StatusStrip> hiçbir paneller vardır.</span><span class="sxs-lookup"><span data-stu-id="5098b-106">The default <xref:System.Windows.Forms.StatusStrip> has no panels.</span></span> <span data-ttu-id="5098b-107">Bölmeleri eklemek için bir <xref:System.Windows.Forms.StatusStrip>, kullanın <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5098b-107">To add panels to a <xref:System.Windows.Forms.StatusStrip>, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="5098b-108">İşleme için kapsamlı destek <xref:System.Windows.Forms.StatusStrip> öğeleri ve Visual Studio yaygın komutları.</span><span class="sxs-lookup"><span data-stu-id="5098b-108">There is extensive support for handling <xref:System.Windows.Forms.StatusStrip> items and common commands in Visual Studio.</span></span>  
  
 <span data-ttu-id="5098b-109">Ayrıca bkz. [StatusStrip öğeleri koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5098b-109">Also see [StatusStrip Items Collection Editor](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip Tasks Dialog Box](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="5098b-110">Ancak <xref:System.Windows.Forms.StatusStrip> değiştirir ve genişletir <xref:System.Windows.Forms.StatusBar> önceki sürümlerinde, denetimin <xref:System.Windows.Forms.StatusBar> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="5098b-110">Although <xref:System.Windows.Forms.StatusStrip> replaces and extends the <xref:System.Windows.Forms.StatusBar> control of previous versions, <xref:System.Windows.Forms.StatusBar> is retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="important-statusstrip-members"></a><span data-ttu-id="5098b-111">Önemli StatusStrip üyeleri</span><span class="sxs-lookup"><span data-stu-id="5098b-111">Important StatusStrip Members</span></span>  
  
|<span data-ttu-id="5098b-112">Ad</span><span class="sxs-lookup"><span data-stu-id="5098b-112">Name</span></span>|<span data-ttu-id="5098b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5098b-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|<span data-ttu-id="5098b-114">Belirten değeri alır veya ayarlar olup olmadığını <xref:System.Windows.Forms.StatusStrip> taşması işlevselliği destekler.</span><span class="sxs-lookup"><span data-stu-id="5098b-114">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|<span data-ttu-id="5098b-115">Belirten değeri alır veya ayarlar olup olmadığını <xref:System.Windows.Forms.StatusStrip> uzatır uçtan uca içinde kendi <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="5098b-115">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> stretches from end to end in its <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
  
### <a name="important-statusstrip-companion-classes"></a><span data-ttu-id="5098b-116">Önemli StatusStrip yardımcı sınıfları</span><span class="sxs-lookup"><span data-stu-id="5098b-116">Important StatusStrip Companion Classes</span></span>  
  
|<span data-ttu-id="5098b-117">Ad</span><span class="sxs-lookup"><span data-stu-id="5098b-117">Name</span></span>|<span data-ttu-id="5098b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5098b-118">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|<span data-ttu-id="5098b-119">Masası'nda temsil eden bir <xref:System.Windows.Forms.StatusStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="5098b-119">Represents a panel in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|<span data-ttu-id="5098b-120">İlişkili bir görüntüler <xref:System.Windows.Forms.ToolStripDropDown> alınacağı kullanıcı tek bir öğe seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5098b-120">Displays an associated <xref:System.Windows.Forms.ToolStripDropDown> from which the user can select a single item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|<span data-ttu-id="5098b-121">Standart bir düğme ve bir açılır menü iki parçalı bir denetimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5098b-121">Represents a two-part control that is a standard button and a drop-down menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|<span data-ttu-id="5098b-122">Bir işleminin tamamlanma durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5098b-122">Displays the completion state of a process.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5098b-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5098b-123">See Also</span></span>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
