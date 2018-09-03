---
title: StatusStrip Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
ms.openlocfilehash: e40373dd05e59325cdb6c2272d5749f3828b0755
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488319"
---
# <a name="statusstrip-control-overview"></a><span data-ttu-id="2608a-102">StatusStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2608a-102">StatusStrip Control Overview</span></span>
<span data-ttu-id="2608a-103">A <xref:System.Windows.Forms.StatusStrip> denetimi, görüntülenmekte olan bir nesneyle ilgili bilgileri görüntüler bir <xref:System.Windows.Forms.Form>, nesnenin bileşenlerini veya nesnenin işlemi uygulamanız içinde ilgili bağlamsal bilgi.</span><span class="sxs-lookup"><span data-stu-id="2608a-103">A <xref:System.Windows.Forms.StatusStrip> control displays information about an object being viewed on a <xref:System.Windows.Forms.Form>, the object's components, or contextual information that relates to that object's operation within your application.</span></span> <span data-ttu-id="2608a-104">Genellikle, bir <xref:System.Windows.Forms.StatusStrip> denetim oluşur <xref:System.Windows.Forms.ToolStripStatusLabel> nesneleri, metin, simge ya da her ikisini de her biri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2608a-104">Typically, a <xref:System.Windows.Forms.StatusStrip> control consists of <xref:System.Windows.Forms.ToolStripStatusLabel> objects, each of which displays text, an icon, or both.</span></span> <span data-ttu-id="2608a-105"><xref:System.Windows.Forms.StatusStrip> De içerebilir <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, ve <xref:System.Windows.Forms.ToolStripProgressBar> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="2608a-105">The <xref:System.Windows.Forms.StatusStrip> can also contain <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, and <xref:System.Windows.Forms.ToolStripProgressBar> controls.</span></span>  
  
 <span data-ttu-id="2608a-106">Varsayılan <xref:System.Windows.Forms.StatusStrip> hiçbir bölmeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="2608a-106">The default <xref:System.Windows.Forms.StatusStrip> has no panels.</span></span> <span data-ttu-id="2608a-107">Panellere eklemek için bir <xref:System.Windows.Forms.StatusStrip>, kullanın <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2608a-107">To add panels to a <xref:System.Windows.Forms.StatusStrip>, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="2608a-108">İşleme için kapsamlı destek <xref:System.Windows.Forms.StatusStrip> öğeleri ve Visual Studio'daki sık kullanılan komutlar.</span><span class="sxs-lookup"><span data-stu-id="2608a-108">There is extensive support for handling <xref:System.Windows.Forms.StatusStrip> items and common commands in Visual Studio.</span></span>  
  
 <span data-ttu-id="2608a-109">Ayrıca bkz: [StatusStrip öğeler Koleksiyonu Düzenleyicisi](https://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip görevleri iletişim kutusu](https://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="2608a-109">Also see [StatusStrip Items Collection Editor](https://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip Tasks Dialog Box](https://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="2608a-110">Ancak <xref:System.Windows.Forms.StatusStrip> değiştirir ve genişleten <xref:System.Windows.Forms.StatusBar> önceki sürümlerinde, denetimin <xref:System.Windows.Forms.StatusBar> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="2608a-110">Although <xref:System.Windows.Forms.StatusStrip> replaces and extends the <xref:System.Windows.Forms.StatusBar> control of previous versions, <xref:System.Windows.Forms.StatusBar> is retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="important-statusstrip-members"></a><span data-ttu-id="2608a-111">StatusStrip önemli üyeleri</span><span class="sxs-lookup"><span data-stu-id="2608a-111">Important StatusStrip Members</span></span>  
  
|<span data-ttu-id="2608a-112">Ad</span><span class="sxs-lookup"><span data-stu-id="2608a-112">Name</span></span>|<span data-ttu-id="2608a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2608a-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|<span data-ttu-id="2608a-114">Belirten bir değeri alır veya ayarlar olmadığını <xref:System.Windows.Forms.StatusStrip> overflow işlevselliği destekler.</span><span class="sxs-lookup"><span data-stu-id="2608a-114">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|<span data-ttu-id="2608a-115">Belirten bir değeri alır veya ayarlar olmadığını <xref:System.Windows.Forms.StatusStrip> uzatır uçtan uca içinde kendi <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="2608a-115">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> stretches from end to end in its <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
  
### <a name="important-statusstrip-companion-classes"></a><span data-ttu-id="2608a-116">Önemli StatusStrip yardımcı sınıfları</span><span class="sxs-lookup"><span data-stu-id="2608a-116">Important StatusStrip Companion Classes</span></span>  
  
|<span data-ttu-id="2608a-117">Ad</span><span class="sxs-lookup"><span data-stu-id="2608a-117">Name</span></span>|<span data-ttu-id="2608a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2608a-118">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|<span data-ttu-id="2608a-119">Bir panel içinde temsil eden bir <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2608a-119">Represents a panel in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|<span data-ttu-id="2608a-120">İlişkili bir görüntüler <xref:System.Windows.Forms.ToolStripDropDown> içinden kullanıcı tek bir öğe seçebilir.</span><span class="sxs-lookup"><span data-stu-id="2608a-120">Displays an associated <xref:System.Windows.Forms.ToolStripDropDown> from which the user can select a single item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|<span data-ttu-id="2608a-121">Standart bir düğme ve bir açılan menü iki parçalı bir denetimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2608a-121">Represents a two-part control that is a standard button and a drop-down menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|<span data-ttu-id="2608a-122">Bir işlemi tamamlama durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2608a-122">Displays the completion state of a process.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2608a-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2608a-123">See Also</span></span>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
