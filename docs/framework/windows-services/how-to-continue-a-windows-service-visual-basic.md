---
title: "Nasıl Yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 73b16a5e5834f7279ae551d4e7efd26cc86c1d07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="377f2-102">Nasıl Yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="377f2-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="377f2-103">Bu örnekte <xref:System.ServiceProcess.ServiceController> IIS Yönetim hizmeti yerel bilgisayarda devam etmek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="377f2-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="377f2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="377f2-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="377f2-105">Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="377f2-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="377f2-106">Kod parçacığı Seçici bulunur **Windows işletim sistemi > Windows Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="377f2-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="377f2-107">Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="377f2-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="377f2-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="377f2-108">Compiling the Code</span></span>  
 <span data-ttu-id="377f2-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="377f2-109">This example requires:</span></span>  
  
-   <span data-ttu-id="377f2-110">System.serviceprocess.dll'ye proje başvurusu.</span><span class="sxs-lookup"><span data-stu-id="377f2-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="377f2-111">Üye erişimi <xref:System.ServiceProcess> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="377f2-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="377f2-112">Ekleme bir `Imports` üye adlarının kodunuzda tam olarak niteleyemiyorsanız deyimi.</span><span class="sxs-lookup"><span data-stu-id="377f2-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="377f2-113">Daha fazla bilgi için bkz: [Imports deyimi (.NET Namespace ve türü)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="377f2-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="377f2-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="377f2-114">Robust Programming</span></span>  
 <span data-ttu-id="377f2-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Özelliği <xref:System.ServiceProcess.ServiceController> sınıfı varsayılan olarak yerel bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="377f2-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="377f2-116">Başka bir bilgisayarda Windows Hizmetleri başvurmak için değiştirme <xref:System.ServiceProcess.ServiceController.MachineName%2A> o bilgisayarın adını özelliğine.</span><span class="sxs-lookup"><span data-stu-id="377f2-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="377f2-117">Çağıramazsınız <xref:System.ServiceProcess.ServiceController.Continue%2A> hizmet denetleyicisi durumu olana kadar bir hizmet yöntemini <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span><span class="sxs-lookup"><span data-stu-id="377f2-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="377f2-118">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="377f2-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="377f2-119">Hizmet sürdürülemez.</span><span class="sxs-lookup"><span data-stu-id="377f2-119">The service cannot be resumed.</span></span> <span data-ttu-id="377f2-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="377f2-120">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="377f2-121">Sistem API erişirken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="377f2-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="377f2-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="377f2-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="377f2-123">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="377f2-123">.NET Framework Security</span></span>  
 <span data-ttu-id="377f2-124">Bilgisayardaki hizmetlerin denetimi kullanarak kısıtlanabilir <xref:System.ServiceProcess.ServiceControllerPermissionAccess> izinleri ayarlamak için numaralandırma <xref:System.ServiceProcess.ServiceControllerPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="377f2-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="377f2-125">Kullanarak hizmet bilgilerine erişim kısıtlanabilir <xref:System.Security.Permissions.PermissionState> izinleri ayarlamak için numaralandırma <xref:System.Security.Permissions.SecurityPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="377f2-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="377f2-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="377f2-126">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [<span data-ttu-id="377f2-127">Nasıl Yapılır: Windows Hizmetini Duraklatma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="377f2-127">How to: Pause a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
