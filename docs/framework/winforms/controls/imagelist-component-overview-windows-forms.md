---
title: "ImageList Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a913de1a6808c7e600a4f28ed58dedf93506466b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imagelist-component-overview-windows-forms"></a><span data-ttu-id="27f68-102">ImageList Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="27f68-102">ImageList Component Overview (Windows Forms)</span></span>
<span data-ttu-id="27f68-103">Windows Forms <xref:System.Windows.Forms.ImageList> bileşen denetimleri tarafından görüntülenebilen görüntüleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="27f68-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is used to store images, which can then be displayed by controls.</span></span> <span data-ttu-id="27f68-104">Görüntü listesi görüntülerinin tek, tutarlı bir katalog için kod yazmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="27f68-104">An image list allows you to write code for a single, consistent catalog of images.</span></span> <span data-ttu-id="27f68-105">Örneğin, tarafından görüntülenen görüntüleri döndürebilirsiniz bir <xref:System.Windows.Forms.Button> düğmenin değiştirerek sadece denetim <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> veya <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="27f68-105">For example, you can rotate images displayed by a <xref:System.Windows.Forms.Button> control simply by changing the button's <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> or <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> property.</span></span> <span data-ttu-id="27f68-106">Ayrıca, aynı resim listesi birden çok denetimleri ile ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27f68-106">You can also associate the same image list with multiple controls.</span></span> <span data-ttu-id="27f68-107">Örneğin, her ikisi de kullanıyorsanız, bir <xref:System.Windows.Forms.ListView> denetim ve <xref:System.Windows.Forms.TreeView> denetimi dosyaları, görüntü listedeki bir dosyanın simgeyi değiştirme aynı listesini görüntülemek için her iki görünümde de görünen için yeni simgesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="27f68-107">For example, if you are using both a <xref:System.Windows.Forms.ListView> control and a <xref:System.Windows.Forms.TreeView> control to display the same list of files, changing a file's icon in the image list will cause the new icon to appear in both views.</span></span>  
  
## <a name="using-imagelist-with-controls"></a><span data-ttu-id="27f68-108">ImageList denetimler ile kullanma</span><span class="sxs-lookup"><span data-stu-id="27f68-108">Using ImageList with Controls</span></span>  
 <span data-ttu-id="27f68-109">Görüntü listesi olan herhangi bir denetimle kullanabilirsiniz bir `ImageList` özelliği — veya durumunda <xref:System.Windows.Forms.ListView> denetimi <xref:System.Windows.Forms.ListView.SmallImageList%2A> ve <xref:System.Windows.Forms.ListView.LargeImageList%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="27f68-109">You can use an image list with any control that has an `ImageList` property — or in the case of the <xref:System.Windows.Forms.ListView> control, <xref:System.Windows.Forms.ListView.SmallImageList%2A> and <xref:System.Windows.Forms.ListView.LargeImageList%2A> properties.</span></span> <span data-ttu-id="27f68-110">Görüntü listesi ile ilişkilendirilebilir denetimleri içerir: <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, ve <xref:System.Windows.Forms.Label> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="27f68-110">The controls that can be associated with an image list include: the <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, and <xref:System.Windows.Forms.Label> controls.</span></span> <span data-ttu-id="27f68-111">Görüntü listesi denetimi ile ilişkilendirmek için denetimin ayarlamak `ImageList` adını özelliğine <xref:System.Windows.Forms.ImageList> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="27f68-111">To associate the image list with a control, set the control's `ImageList` property to the name of the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="27f68-112">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="27f68-112">Key Properties</span></span>  
 <span data-ttu-id="27f68-113">Anahtar özelliği <xref:System.Windows.Forms.ImageList> bileşeni <xref:System.Windows.Forms.ImageList.Images%2A>, ilişkili denetimi tarafından kullanılacak resimler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="27f68-113">The key property of the <xref:System.Windows.Forms.ImageList> component is <xref:System.Windows.Forms.ImageList.Images%2A>, which contains the pictures to be used by the associated control.</span></span> <span data-ttu-id="27f68-114">Tek tek her görüntü dizini değerini veya kendi anahtar tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="27f68-114">Each individual image can be accessed by its index value or by its key.</span></span> <span data-ttu-id="27f68-115"><xref:System.Windows.Forms.ImageList.ColorDepth%2A> Özelliği, görüntüleri ile işlenen renk sayısını belirler.</span><span class="sxs-lookup"><span data-stu-id="27f68-115">The <xref:System.Windows.Forms.ImageList.ColorDepth%2A> property determines the number of colors that the images are rendered with.</span></span> <span data-ttu-id="27f68-116">Görüntüleri tüm tarafından belirlenen aynı boyutta görüntülenir <xref:System.Windows.Forms.ImageList.ImageSize%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="27f68-116">The images will all be displayed at the same size, set by the <xref:System.Windows.Forms.ImageList.ImageSize%2A> property.</span></span> <span data-ttu-id="27f68-117">Daha büyük görüntüleri uyacak şekilde ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="27f68-117">Images that are larger will be scaled to fit.</span></span>  
  
 <span data-ttu-id="27f68-118">Kullanıyorsanız [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], uygulamalarınızda kullanabileceğiniz standart görüntüleri büyük kitaplığı erişimi.</span><span class="sxs-lookup"><span data-stu-id="27f68-118">If you are using [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you have access to a large library of standard images that you can use in your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f68-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27f68-119">See Also</span></span>  
 <xref:System.Windows.Forms.ImageList>  
 [<span data-ttu-id="27f68-120">Nasıl yapılır: Windows Forms ImageList Bileşeni ile Görüntü Ekleme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="27f68-120">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
