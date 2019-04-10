---
title: 'Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
ms.openlocfilehash: 131dc688d2a742fa7a0d99ec7858d4e280c9882f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310765"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="80462-102">Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama</span><span class="sxs-lookup"><span data-stu-id="80462-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="80462-103">Çalıştırılmaya hazır olduğunu form oluşturmaya uluslararası pazarlar için geliştirme hızını büyük ölçüde yerelleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="80462-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="80462-104">Kullanabileceğiniz <xref:System.Windows.Forms.TableLayoutPanel> denetim değişiklikleri nedeniyle denetimleri yeniden boyutlandırma sırasında düzgün bir şekilde yanıt düzenleri uygulamak için kendi <xref:System.Windows.Forms.Control.Text%2A> özellik değerleri.</span><span class="sxs-lookup"><span data-stu-id="80462-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80462-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="80462-105">Example</span></span>  
 <span data-ttu-id="80462-106">Bu formu görüntülenen dize değerlerini diğer dillere çevirme, orantılı olarak ayarlayan bir düzen oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="80462-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="80462-107">Bu işlem çevirisi çağrılırken *yerelleştirme*.</span><span class="sxs-lookup"><span data-stu-id="80462-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="80462-108">Daha fazla bilgi için [yerelleştirme](../../../standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="80462-108">For more information, see [Localization](../../../standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="80462-109">Visual Studio'da bu görevi için kapsamlı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="80462-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="80462-110">Ayrıca bkz: [izlenecek yol: Bir düzen oluşturma, yerelleştirme için oranı ayarlayan](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="80462-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a><span data-ttu-id="80462-111">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="80462-111">Additional resources</span></span>
1. [<span data-ttu-id="80462-112">Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma</span><span class="sxs-lookup"><span data-stu-id="80462-112">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="80462-113">İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="80462-113">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [<span data-ttu-id="80462-114">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma</span><span class="sxs-lookup"><span data-stu-id="80462-114">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="80462-115">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="80462-115">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [<span data-ttu-id="80462-116">İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="80462-116">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [<span data-ttu-id="80462-117">İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="80462-117">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [<span data-ttu-id="80462-118">İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Forms Denetimlerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="80462-118">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)  
  
8. [<span data-ttu-id="80462-119">Nasıl yapılır: AutoSize ve TableLayoutPanel denetimini kullanarak Windows Formları yerelleştirme desteği</span><span class="sxs-lookup"><span data-stu-id="80462-119">How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [<span data-ttu-id="80462-120">İzlenecek yol: Veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma</span><span class="sxs-lookup"><span data-stu-id="80462-120">Walkthrough: Creating a Resizable Windows Form for Data Entry</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a><span data-ttu-id="80462-121">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="80462-121">Compiling the Code</span></span>  
 <span data-ttu-id="80462-122">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="80462-122">This example requires:</span></span>  
  
-   <span data-ttu-id="80462-123">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="80462-123">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="80462-124">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="80462-124">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="80462-125">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80462-125">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80462-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80462-126">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="80462-127">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="80462-127">Localization</span></span>](../../../standard/globalization-localization/localization.md)
