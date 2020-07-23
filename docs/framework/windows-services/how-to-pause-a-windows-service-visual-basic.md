---
title: 'Nasıl yapılır: Windows Hizmetini Duraklatma (Visual Basic)'
description: Visual Basic sahip yerel bir bilgisayarda bir Windows hizmetini (IIS Yönetim hizmeti gibi) duraklatmak için ServiceController bileşenini nasıl kullanacağınızı okuyun.
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
author: ghogen
ms.openlocfilehash: 628cc2e896f7f8a289e52674b721c4aef605854c
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925572"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="71f3f-103">Nasıl yapılır: Windows Hizmetini Duraklatma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71f3f-103">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="71f3f-104">Bu örnek, <xref:System.ServiceProcess.ServiceController> bileşeni yerel BILGISAYARDAKI IIS Yöneticisi hizmetini duraklatmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="71f3f-104">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71f3f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="71f3f-105">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="71f3f-106">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71f3f-106">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="71f3f-107">Kod parçacığı seçicide, Windows **Işletim sistemi > Windows Hizmetleri**' nde bulunur.</span><span class="sxs-lookup"><span data-stu-id="71f3f-107">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="71f3f-108">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="71f3f-108">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="71f3f-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="71f3f-109">Compiling the Code</span></span>  
 <span data-ttu-id="71f3f-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="71f3f-110">This example requires:</span></span>  
  
- <span data-ttu-id="71f3f-111">System.serviceprocess.dll bir proje başvurusu.</span><span class="sxs-lookup"><span data-stu-id="71f3f-111">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="71f3f-112"><xref:System.ServiceProcess>Ad alanının üyelerine erişin.</span><span class="sxs-lookup"><span data-stu-id="71f3f-112">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="71f3f-113">`Imports`Kodunuzda üye adlarını tam olarak nitedıysanız bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="71f3f-113">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="71f3f-114">Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="71f3f-114">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="71f3f-115">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="71f3f-115">Robust Programming</span></span>  
 <span data-ttu-id="71f3f-116"><xref:System.ServiceProcess.ServiceController.MachineName%2A>Sınıfının özelliği, <xref:System.ServiceProcess.ServiceController> Varsayılan olarak yerel bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="71f3f-116">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="71f3f-117">Başka bir bilgisayardaki Windows hizmetlerine başvurmak için, <xref:System.ServiceProcess.ServiceController.MachineName%2A> özelliği bu bilgisayarın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="71f3f-117">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="71f3f-118">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="71f3f-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="71f3f-119">Hizmet duraklatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="71f3f-119">The service cannot be paused.</span></span> <span data-ttu-id="71f3f-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="71f3f-120">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="71f3f-121">Sistem API 'sine erişirken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="71f3f-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="71f3f-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="71f3f-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="71f3f-123">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="71f3f-123">.NET Framework Security</span></span>  
 <span data-ttu-id="71f3f-124">Bilgisayardaki hizmetlerin denetimi, <xref:System.ServiceProcess.ServiceControllerPermissionAccess> içindeki izinleri ayarlamak için kullanılarak kısıtlanabilir <xref:System.ServiceProcess.ServiceControllerPermission> .</span><span class="sxs-lookup"><span data-stu-id="71f3f-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="71f3f-125">Hizmet bilgilerine erişim, <xref:System.Security.Permissions.PermissionState> içindeki izinleri ayarlamak için kullanılarak kısıtlanabilir <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="71f3f-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f3f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71f3f-126">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="71f3f-127">Nasıl yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71f3f-127">How to: Continue a Windows Service (Visual Basic)</span></span>](how-to-continue-a-windows-service-visual-basic.md)
