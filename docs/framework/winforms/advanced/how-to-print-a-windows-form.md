---
title: "Nasıl yapılır: Bir Windows Formunu Yazdırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c50b1f47d207334160ed12674ee8efb1390fb84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="a6487-102">Nasıl yapılır: Bir Windows Formunu Yazdırma</span><span class="sxs-lookup"><span data-stu-id="a6487-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="a6487-103">Geliştirme sürecinin bir parçası olarak, genellikle Windows formu bir kopyasını yazdırmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="a6487-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="a6487-104">Aşağıdaki kod örneğinde geçerli formun bir kopyasını kullanarak yazdırma gösterilmektedir <xref:System.Drawing.Graphics.CopyFromScreen%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a6487-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6487-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6487-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a6487-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a6487-106">Compiling the Code</span></span>  
 <span data-ttu-id="a6487-107">Bu içeren bir tam bir kod örneğidir bir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a6487-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a6487-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="a6487-108">Robust Programming</span></span>  
 <span data-ttu-id="a6487-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="a6487-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="a6487-110">Yazıcı erişim iznine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="a6487-110">You do not have permission to access the printer.</span></span>  
  
-   <span data-ttu-id="a6487-111">Yazıcı yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="a6487-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a6487-112">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a6487-112">.NET Framework Security</span></span>  
 <span data-ttu-id="a6487-113">Bu kod örneği çalıştırmak için bilgisayarınızda kullandığınız yazıcıya erişim izni olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6487-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6487-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6487-114">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="a6487-115">Nasıl yapılır: GDI+ ile Görüntü İşleme</span><span class="sxs-lookup"><span data-stu-id="a6487-115">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [<span data-ttu-id="a6487-116">Nasıl yapılır: Windows Forms'ta Grafik Yazdırma</span><span class="sxs-lookup"><span data-stu-id="a6487-116">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
