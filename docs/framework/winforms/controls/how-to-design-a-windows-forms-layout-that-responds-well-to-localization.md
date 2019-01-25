---
title: 'Nasıl yapılır: Yerelleştirmeye iyi cevap veren bir Windows Forms düzeni tasarlama'
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
ms.openlocfilehash: 15f290f7d076eede7a8092d7295df810e4e51bf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563528"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="f0451-102">Nasıl yapılır: Yerelleştirmeye iyi cevap veren bir Windows Forms düzeni tasarlama</span><span class="sxs-lookup"><span data-stu-id="f0451-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="f0451-103">Çalıştırılmaya hazır olduğunu form oluşturmaya uluslararası pazarlar için geliştirme hızını büyük ölçüde yerelleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="f0451-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="f0451-104">Kullanabileceğiniz <xref:System.Windows.Forms.TableLayoutPanel> denetim değişiklikleri nedeniyle denetimleri yeniden boyutlandırma sırasında düzgün bir şekilde yanıt düzenleri uygulamak için kendi <xref:System.Windows.Forms.Control.Text%2A> özellik değerleri.</span><span class="sxs-lookup"><span data-stu-id="f0451-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0451-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0451-105">Example</span></span>  
 <span data-ttu-id="f0451-106">Bu formu görüntülenen dize değerlerini diğer dillere çevirme, orantılı olarak ayarlayan bir düzen oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0451-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="f0451-107">Bu işlem çevirisi çağrılırken *yerelleştirme*.</span><span class="sxs-lookup"><span data-stu-id="f0451-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="f0451-108">Daha fazla bilgi için [yerelleştirme](../../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="f0451-108">For more information, see [Localization](../../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="f0451-109">Visual Studio'da bu görevi için kapsamlı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="f0451-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="f0451-110">Ayrıca bkz: [izlenecek yol: Bir düzen oluşturma, yerelleştirme için oranı ayarlayan](https://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f0451-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  [<span data-ttu-id="f0451-111">Nasıl yapılır: Hizalama ve denetim TableLayoutPanel denetiminde uzatma</span><span class="sxs-lookup"><span data-stu-id="f0451-111">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  <span data-ttu-id="f0451-112">[İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="f0451-112">[Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span></span>  
  
3.  [<span data-ttu-id="f0451-113">Nasıl yapılır: TableLayoutPanel denetimi içindeki satırları ve sütunları span</span><span class="sxs-lookup"><span data-stu-id="f0451-113">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4.  [<span data-ttu-id="f0451-114">Nasıl yapılır: Bir TableLayoutPanel denetimindeki satırları ve sütunları Düzenle</span><span class="sxs-lookup"><span data-stu-id="f0451-114">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5.  <span data-ttu-id="f0451-115">[İzlenecek yol: Üzerinde Windows Forms denetimleri etiketleri akıllı kullanarak ortak görevleri gerçekleştirme](https://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="f0451-115">[Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](https://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span></span>  
  
6.  <span data-ttu-id="f0451-116">[İzlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="f0451-116">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
7.  <span data-ttu-id="f0451-117">[İzlenecek yol: Windows Forms denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile düzenleme](https://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="f0451-117">[Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](https://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span></span>  
  
8.  <span data-ttu-id="f0451-118">[Nasıl yapılır: AutoSize ve TableLayoutPanel denetimini kullanarak Windows Formları yerelleştirme desteği](https://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="f0451-118">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span></span>  
  
9. <span data-ttu-id="f0451-119">[İzlenecek yol: Veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="f0451-119">[Walkthrough: Creating a Resizable Windows Form for Data Entry](https://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f0451-120">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f0451-120">Compiling the Code</span></span>  
 <span data-ttu-id="f0451-121">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f0451-121">This example requires:</span></span>  
  
-   <span data-ttu-id="f0451-122">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="f0451-122">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f0451-123">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f0451-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f0451-124">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0451-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="f0451-125">Ayrıca bkz: [nasıl yapılır: Derleme ve Visual Studio kullanarak tam bir Windows Formları kod örneği çalıştırma](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f0451-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0451-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0451-126">See also</span></span>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="f0451-127">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="f0451-127">Localization</span></span>](../../../../docs/standard/globalization-localization/localization.md)
