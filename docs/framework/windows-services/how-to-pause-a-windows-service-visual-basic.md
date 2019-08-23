---
title: 'Nasıl yapılır: Windows Hizmetini Duraklatma (Visual Basic)'
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
ms.openlocfilehash: 20bc177ccf2646f79994553803568531233ea5c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935477"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="acf86-102">Nasıl yapılır: Windows Hizmetini Duraklatma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acf86-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="acf86-103">Bu örnek, <xref:System.ServiceProcess.ServiceController> bileşeni yerel bilgisayardaki IIS Yöneticisi hizmetini duraklatmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="acf86-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acf86-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="acf86-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="acf86-105">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acf86-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="acf86-106">Kod parçacığı seçicide, Windows **Işletim sistemi > Windows Hizmetleri**' nde bulunur.</span><span class="sxs-lookup"><span data-stu-id="acf86-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="acf86-107">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="acf86-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="acf86-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="acf86-108">Compiling the Code</span></span>  
 <span data-ttu-id="acf86-109">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="acf86-109">This example requires:</span></span>  
  
- <span data-ttu-id="acf86-110">System. ServiceProcess. dll dosyasına bir proje başvurusu.</span><span class="sxs-lookup"><span data-stu-id="acf86-110">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="acf86-111"><xref:System.ServiceProcess> Ad alanının üyelerine erişin.</span><span class="sxs-lookup"><span data-stu-id="acf86-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="acf86-112">Kodunuzda üye `Imports` adlarını tam olarak nitedıysanız bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="acf86-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="acf86-113">Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="acf86-113">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="acf86-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="acf86-114">Robust Programming</span></span>  
 <span data-ttu-id="acf86-115"><xref:System.ServiceProcess.ServiceController> Sınıfının özelliği, varsayılan olarak yerel bilgisayardır. <xref:System.ServiceProcess.ServiceController.MachineName%2A></span><span class="sxs-lookup"><span data-stu-id="acf86-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="acf86-116">Başka bir bilgisayardaki Windows hizmetlerine başvurmak için, <xref:System.ServiceProcess.ServiceController.MachineName%2A> özelliği bu bilgisayarın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="acf86-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="acf86-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="acf86-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="acf86-118">Hizmet duraklatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="acf86-118">The service cannot be paused.</span></span> <span data-ttu-id="acf86-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="acf86-119">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="acf86-120">Sistem API 'sine erişirken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="acf86-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="acf86-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="acf86-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="acf86-122">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="acf86-122">.NET Framework Security</span></span>  
 <span data-ttu-id="acf86-123">Bilgisayardaki hizmetlerin denetimi, <xref:System.ServiceProcess.ServiceControllerPermissionAccess> <xref:System.ServiceProcess.ServiceControllerPermission>içindeki izinleri ayarlamak için kullanılarak kısıtlanabilir.</span><span class="sxs-lookup"><span data-stu-id="acf86-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="acf86-124">Hizmet bilgilerine erişim, <xref:System.Security.Permissions.PermissionState> <xref:System.Security.Permissions.SecurityPermission>içindeki izinleri ayarlamak için kullanılarak kısıtlanabilir.</span><span class="sxs-lookup"><span data-stu-id="acf86-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acf86-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acf86-125">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="acf86-126">Nasıl yapılır: Bir Windows hizmetine devam et (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acf86-126">How to: Continue a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
