---
title: Yerelleştirme kullanımı kolay bir düzen tasarlama
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
ms.openlocfilehash: 36ffd532b9f539107307144d25c8d9d5f8ba634a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743288"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="10f2f-102">Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama</span><span class="sxs-lookup"><span data-stu-id="10f2f-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="10f2f-103">Yerelleştirmeye izin veren formların oluşturulması uluslararası pazarlar için geliştirmeyi büyük ölçüde hızlandırır.</span><span class="sxs-lookup"><span data-stu-id="10f2f-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="10f2f-104">Denetim yeniden boyutlandırılması, <xref:System.Windows.Forms.Control.Text%2A> özellik değerlerindeki değişiklikler nedeniyle düzgün şekilde yanıt veren düzenler uygulamak için <xref:System.Windows.Forms.TableLayoutPanel> denetimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10f2f-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10f2f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="10f2f-105">Example</span></span>  
 <span data-ttu-id="10f2f-106">Bu form, görüntülenen dize değerlerini diğer dillere çevirecek zaman orantılı olarak ayarlayan bir düzen oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="10f2f-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="10f2f-107">Bu çeviri işlemine *Yerelleştirme*denir.</span><span class="sxs-lookup"><span data-stu-id="10f2f-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="10f2f-108">Daha fazla bilgi için bkz. [Yerelleştirme](../../../standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="10f2f-108">For more information, see [Localization](../../../standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="10f2f-109">Visual Studio 'da bu görev için kapsamlı destek vardır.</span><span class="sxs-lookup"><span data-stu-id="10f2f-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="10f2f-110">Ayrıca bkz. [Izlenecek yol: yerelleştirme Için orantı ayarlayan bir düzen oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="10f2f-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a><span data-ttu-id="10f2f-111">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="10f2f-111">Additional resources</span></span>

1. [<span data-ttu-id="10f2f-112">Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma</span><span class="sxs-lookup"><span data-stu-id="10f2f-112">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="10f2f-113">İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="10f2f-113">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [<span data-ttu-id="10f2f-114">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma</span><span class="sxs-lookup"><span data-stu-id="10f2f-114">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="10f2f-115">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="10f2f-115">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [<span data-ttu-id="10f2f-116">İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="10f2f-116">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [<span data-ttu-id="10f2f-117">İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="10f2f-117">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [<span data-ttu-id="10f2f-118">İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Forms Denetimlerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="10f2f-118">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)  
  
8. <span data-ttu-id="10f2f-119">[Nasıl yapılır: AutoSize ve TableLayoutPanel denetimini kullanarak Windows Forms yerelleştirmeyi destekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10f2f-119">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span></span>  
  
9. <span data-ttu-id="10f2f-120">[İzlenecek yol: veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10f2f-120">[Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="10f2f-121">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="10f2f-121">Compiling the Code</span></span>  
 <span data-ttu-id="10f2f-122">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="10f2f-122">This example requires:</span></span>  
  
- <span data-ttu-id="10f2f-123">System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="10f2f-123">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f2f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10f2f-124">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="10f2f-125">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="10f2f-125">Localization</span></span>](../../../standard/globalization-localization/localization.md)
