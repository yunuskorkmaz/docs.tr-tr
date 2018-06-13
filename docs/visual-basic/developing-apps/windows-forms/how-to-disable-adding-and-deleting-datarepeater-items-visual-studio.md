---
title: 'Nasıl Yapılır: DataRepeater Öğelerini Eklemeyi ve Silmeyi Devre Dışı Bırakma (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
ms.openlocfilehash: e3d0d2a8d422054e269ee92df1fdfcb5acb96eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590817"
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a><span data-ttu-id="bf476-102">Nasıl Yapılır: DataRepeater Öğelerini Eklemeyi ve Silmeyi Devre Dışı Bırakma (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="bf476-102">How to: Disable Adding and Deleting DataRepeater Items (Visual Studio)</span></span>
<span data-ttu-id="bf476-103">Varsayılan olarak, kullanıcılar ekleyebilir ve öğeleri silmek bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="bf476-103">By default, users can add and delete items in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="bf476-104">Kullanıcılar, CTRL + N tuşlarına basarak yeni bir öğe ekleyebilirsiniz olduğunda bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> odağa sahip veya tıklayarak **AddNew-Item** düğmesini <xref:System.Windows.Forms.BindingNavigator> denetim.</span><span class="sxs-lookup"><span data-stu-id="bf476-104">Users can add a new item by pressing CTRL+N when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **AddNewItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span> <span data-ttu-id="bf476-105">Kullanıcıları, bir öğe tuşlarına basarak silebilir ne zaman silmek bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> odağa sahip veya tıklayarak **DeleteItem** düğmesini <xref:System.Windows.Forms.BindingNavigator> denetim.</span><span class="sxs-lookup"><span data-stu-id="bf476-105">Users can delete an item by pressing DELETE when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **DeleteItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
 <span data-ttu-id="bf476-106">Ekleme ve/veya tasarım zamanında veya çalışma zamanında silme devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf476-106">You can disable adding and/or deleting at design time or at run time.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a><span data-ttu-id="bf476-107">Eklemeyi ve tasarım zamanında silmeyi devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="bf476-107">To disable adding and deleting at design time</span></span>  
  
1.  <span data-ttu-id="bf476-108">Windows Forms Tasarımcısı'nda seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="bf476-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf476-109">Denetim alt bölümünü seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf476-109">You must select the lower section of the control.</span></span> <span data-ttu-id="bf476-110">Öğesi şablonu bölümüne seçerseniz, farklı bir özellikler kümesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bf476-110">If you select the item template section, a different set of properties will be displayed.</span></span>  
  
2.  <span data-ttu-id="bf476-111">Özellikler penceresinde ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> özelliğine **False**.</span><span class="sxs-lookup"><span data-stu-id="bf476-111">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> property to **False**.</span></span>  
  
3.  <span data-ttu-id="bf476-112">Ayarlama <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> özelliğine **False**.</span><span class="sxs-lookup"><span data-stu-id="bf476-112">Set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> property to **False**.</span></span>  
  
4.  <span data-ttu-id="bf476-113">Windows Forms Tasarımcısı'nda seçin <xref:System.Windows.Forms.BindingNavigator> denetlemek ve ardından **AddNew-Item** düğmesini (düğmesi üzerindeki bir artı işareti olan).</span><span class="sxs-lookup"><span data-stu-id="bf476-113">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **AddNewItem** button (the button with a plus sign on it).</span></span>  
  
5.  <span data-ttu-id="bf476-114">Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> özelliğine **False**.</span><span class="sxs-lookup"><span data-stu-id="bf476-114">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
6.  <span data-ttu-id="bf476-115">Windows Forms Tasarımcısı'nda seçin <xref:System.Windows.Forms.BindingNavigator> denetlemek ve ardından **DeleteItem** düğmesini (düğmesi, kırmızı bir X ile).</span><span class="sxs-lookup"><span data-stu-id="bf476-115">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **DeleteItem** button (the button with a red X on it).</span></span>  
  
7.  <span data-ttu-id="bf476-116">Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> özelliğine **False**.</span><span class="sxs-lookup"><span data-stu-id="bf476-116">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
8.  <span data-ttu-id="bf476-117">Bileşen tepsisinde seçin <xref:System.Windows.Forms.BindingSource> hangi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf476-117">In the Component Tray, select the <xref:System.Windows.Forms.BindingSource> to which the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is bound.</span></span>  
  
9. <span data-ttu-id="bf476-118">Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.BindingSource.AllowNew%2A> özelliğine **False**.</span><span class="sxs-lookup"><span data-stu-id="bf476-118">In the Properties window, set the <xref:System.Windows.Forms.BindingSource.AllowNew%2A> property to **False**.</span></span>  
  
10. <span data-ttu-id="bf476-119">Windows Forms Tasarımcısı'nda çift **DeleteItem** düğmesi kod düzenleyicisini açın.</span><span class="sxs-lookup"><span data-stu-id="bf476-119">In the Windows Forms Designer, double-click the **DeleteItem** button to open the Code Editor.</span></span>  
  
11. <span data-ttu-id="bf476-120">Olayları aşağı açılan listesinde seçin `BindingNavigatorDeleteItem_EnabledChanged` olay.</span><span class="sxs-lookup"><span data-stu-id="bf476-120">In the Events drop-down list, select the `BindingNavigatorDeleteItem_EnabledChanged` event.</span></span>  
  
12. <span data-ttu-id="bf476-121">Aşağıdaki kodu ekleyin `BindingNavigatorDeleteItem_EnabledChanged` olay işleyicisi:</span><span class="sxs-lookup"><span data-stu-id="bf476-121">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="bf476-122">Bu adım gereklidir çünkü <xref:System.Windows.Forms.BindingSource> etkinleştirecek **DeleteItem** düğmesini geçerli kayıt değişiklikleri her zaman.</span><span class="sxs-lookup"><span data-stu-id="bf476-122">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a><span data-ttu-id="bf476-123">Ekleme ve çalışma zamanında silme devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="bf476-123">To disable adding and deleting at run time</span></span>  
  
1.  <span data-ttu-id="bf476-124">Windows Forms Tasarımcısı'nda formun Kod Düzenleyicisi'ni açmak için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bf476-124">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="bf476-125">Aşağıdaki kodu ekleyin `Form_Load` olay:</span><span class="sxs-lookup"><span data-stu-id="bf476-125">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  <span data-ttu-id="bf476-126">Aşağıdaki kodu ekleyin `BindingNavigatorDeleteItem_EnabledChanged` olay işleyicisi:</span><span class="sxs-lookup"><span data-stu-id="bf476-126">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="bf476-127">Bu adım gereklidir çünkü <xref:System.Windows.Forms.BindingSource> etkinleştirecek **DeleteItem** düğmesini geçerli kayıt değişiklikleri her zaman.</span><span class="sxs-lookup"><span data-stu-id="bf476-127">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf476-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf476-128">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="bf476-129">DataRepeater Denetimine Giriş</span><span class="sxs-lookup"><span data-stu-id="bf476-129">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="bf476-130">DataRepeater Denetiminde Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="bf476-130">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
