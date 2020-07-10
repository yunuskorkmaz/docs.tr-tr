---
title: 'Nasıl yapılır: Bir Windows Formunu Yazdırma'
description: CopyFromScreen metodunu kullanarak geçerli Windows formunun bir kopyasının programlı bir şekilde nasıl yazdırılacağını öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: b59ea4b5347903b36a166c4f8ac0d8d7db18635e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174698"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="01d70-103">Nasıl yapılır: Bir Windows Formunu Yazdırma</span><span class="sxs-lookup"><span data-stu-id="01d70-103">How to: Print a Windows Form</span></span>
<span data-ttu-id="01d70-104">Geliştirme sürecinin bir parçası olarak, genellikle Windows formunuzun bir kopyasını yazdırmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="01d70-104">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="01d70-105">Aşağıdaki kod örneğinde, yöntemi kullanılarak geçerli formun bir kopyasının nasıl yazdırılacağı gösterilmektedir <xref:System.Drawing.Graphics.CopyFromScreen%2A> .</span><span class="sxs-lookup"><span data-stu-id="01d70-105">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01d70-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="01d70-106">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="01d70-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="01d70-107">Robust Programming</span></span>  
 <span data-ttu-id="01d70-108">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="01d70-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="01d70-109">Yazıcıya erişim izniniz yok.</span><span class="sxs-lookup"><span data-stu-id="01d70-109">You do not have permission to access the printer.</span></span>  
  
- <span data-ttu-id="01d70-110">Yüklü bir yazıcı yok.</span><span class="sxs-lookup"><span data-stu-id="01d70-110">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="01d70-111">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="01d70-111">.NET Framework Security</span></span>  
 <span data-ttu-id="01d70-112">Bu kod örneğini çalıştırmak için, bilgisayarınızda kullandığınız yazıcıya erişim izninizin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="01d70-112">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d70-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01d70-113">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="01d70-114">Nasıl yapılır: GDI+ ile Görüntü İşleme</span><span class="sxs-lookup"><span data-stu-id="01d70-114">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="01d70-115">Nasıl yapılır: Windows Forms'ta Grafik Yazdırma</span><span class="sxs-lookup"><span data-stu-id="01d70-115">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)
