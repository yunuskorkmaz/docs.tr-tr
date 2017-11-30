---
title: "Nasıl Yapılır: DataRepeater Denetiminde Veri Arama (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3ed7138c142a83584ecd19ccaebe0e31e421ce3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="1e29e-102">Nasıl Yapılır: DataRepeater Denetiminde Veri Arama (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="1e29e-102">How to: Search Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="1e29e-103">Kullanırken bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> belirli bir kayıt let kullanıcıları aramak istediğiniz çok sayıda kayıt içeren denetimi.</span><span class="sxs-lookup"><span data-stu-id="1e29e-103">When you are using a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that contains many records, you may want to let users search for a specific record.</span></span> <span data-ttu-id="1e29e-104">Denetiminde veri arama yerine, bir arama arka plandaki sorgulayarak uygulayabileceğiniz <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="1e29e-104">Rather than searching the data in the control itself, you can implement a search by querying the underlying <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="1e29e-105">Öğe bulunursa, daha sonra kullanabilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> özelliğini öğeyi seçin ve görünümüne gidin.</span><span class="sxs-lookup"><span data-stu-id="1e29e-105">If the item is found, you can then use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> property to select the item and scroll it into view.</span></span>  
  
### <a name="to-implement-search"></a><span data-ttu-id="1e29e-106">Arama uygulamak için</span><span class="sxs-lookup"><span data-stu-id="1e29e-106">To implement search</span></span>  
  
1.  <span data-ttu-id="1e29e-107">Sürükleme bir <xref:System.Windows.Forms.TextBox> gelen denetim **araç** içeren forma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="1e29e-107">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="1e29e-108">Özellikler penceresinde değiştirin **adı** özelliğine **SearchTextBox**.</span><span class="sxs-lookup"><span data-stu-id="1e29e-108">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="1e29e-109">Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** içeren forma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="1e29e-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="1e29e-110">Özellikler penceresinde değiştirin **adı** özelliğine **SearchButton**.</span><span class="sxs-lookup"><span data-stu-id="1e29e-110">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="1e29e-111">Değişiklik **metin** özelliğine **arama**.</span><span class="sxs-lookup"><span data-stu-id="1e29e-111">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="1e29e-112">Çift <xref:System.Windows.Forms.Button> Kod Düzenleyicisi'ni açmak için Denetim ve aşağıdaki kodu ekleyin `SearchButton_Click` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1e29e-112">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     <span data-ttu-id="1e29e-113">Değiştir *ProductsBindingSource* adıyla <xref:System.Windows.Forms.BindingSource> için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>ve Değiştir *ProductID* aramak istediğiniz alanın adı.</span><span class="sxs-lookup"><span data-stu-id="1e29e-113">Replace *ProductsBindingSource* with the name of the <xref:System.Windows.Forms.BindingSource> for your <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and replace *ProductID* with the name of the field that you want to search.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e29e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e29e-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="1e29e-115">DataRepeater denetimine giriş</span><span class="sxs-lookup"><span data-stu-id="1e29e-115">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1e29e-116">DataRepeater denetiminde sorun giderme</span><span class="sxs-lookup"><span data-stu-id="1e29e-116">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1e29e-117">Nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="1e29e-117">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
