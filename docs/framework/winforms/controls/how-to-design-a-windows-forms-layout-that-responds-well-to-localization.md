---
title: 'Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7f35a61c4ef8bbda544e36939fe4986a1017fe31
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="c46c0-102">Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama</span><span class="sxs-lookup"><span data-stu-id="c46c0-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="c46c0-103">Olması hazırsınız formları oluşturma hızları geliştirme uluslararası pazarda için büyük ölçüde yerelleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="c46c0-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="c46c0-104">Kullanabileceğiniz <xref:System.Windows.Forms.TableLayoutPanel> değişiklikleri nedeniyle denetimlerinin boyutunu değiştirme gibi düzgün bir şekilde yanıt düzenleri uygulamak için denetim kendi <xref:System.Windows.Forms.Control.Text%2A> özellik değerleri.</span><span class="sxs-lookup"><span data-stu-id="c46c0-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c46c0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c46c0-105">Example</span></span>  
 <span data-ttu-id="c46c0-106">Bu form nasıl görüntülenen dize değerlerini diğer dillere çevirme yükleyen orantılı olarak ayarlayan bir düzen oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c46c0-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="c46c0-107">Çevirisi, bu işlem çağrılırken *yerelleştirme*.</span><span class="sxs-lookup"><span data-stu-id="c46c0-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="c46c0-108">Daha fazla bilgi için bkz: [yerelleştirme](../../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="c46c0-108">For more information, see [Localization](../../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="c46c0-109">Visual Studio'da bu görev için kapsamlı destek yoktur.</span><span class="sxs-lookup"><span data-stu-id="c46c0-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="c46c0-110">Ayrıca bkz. [izlenecek yol: bir düzen oluşturma oranda yerelleştirme için ayarlar](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="c46c0-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  <span data-ttu-id="c46c0-111">[Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="c46c0-111">[How to: Align and Stretch a Control in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span></span>  
  
2.  <span data-ttu-id="c46c0-112">[İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="c46c0-112">[Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span></span>  
  
3.  <span data-ttu-id="c46c0-113">[Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="c46c0-113">[How to: Span Rows and Columns in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span></span>  
  
4.  <span data-ttu-id="c46c0-114">[Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="c46c0-114">[How to: Edit Columns and Rows in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span></span>  
  
5.  <span data-ttu-id="c46c0-115">[İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="c46c0-115">[Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span></span>  
  
6.  <span data-ttu-id="c46c0-116">[İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="c46c0-116">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
7.  <span data-ttu-id="c46c0-117">[İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Forms Denetimlerini Düzenleme](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="c46c0-117">[Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span></span>  
  
8.  <span data-ttu-id="c46c0-118">[Nasıl yapılır: AutoSize ve TableLayoutPanel denetimi kullanarak Windows Forms'ta yerelleştirme desteği](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="c46c0-118">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span></span>  
  
9. <span data-ttu-id="c46c0-119">[İzlenecek yol: veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="c46c0-119">[Walkthrough: Creating a Resizable Windows Form for Data Entry](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c46c0-120">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c46c0-120">Compiling the Code</span></span>  
 <span data-ttu-id="c46c0-121">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c46c0-121">This example requires:</span></span>  
  
-   <span data-ttu-id="c46c0-122">Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="c46c0-122">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="c46c0-123">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c46c0-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c46c0-124">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c46c0-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="c46c0-125">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="c46c0-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c46c0-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c46c0-126">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [<span data-ttu-id="c46c0-127">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="c46c0-127">Localization</span></span>](../../../../docs/standard/globalization-localization/localization.md)
