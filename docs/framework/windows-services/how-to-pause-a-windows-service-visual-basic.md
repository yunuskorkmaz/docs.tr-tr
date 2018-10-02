---
title: 'Nasıl Yapılır: Windows Hizmetini Duraklatma (Visual Basic)'
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
ms.openlocfilehash: c62de97439ecf90ebfcc14d9fea4c5ab52f6ef73
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035129"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="c358b-102">Nasıl Yapılır: Windows Hizmetini Duraklatma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c358b-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="c358b-103">Bu örnekte <xref:System.ServiceProcess.ServiceController> yerel bilgisayarda IIS Yönetici Hizmeti duraklatma bileşeni.</span><span class="sxs-lookup"><span data-stu-id="c358b-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c358b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c358b-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="c358b-105">Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c358b-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c358b-106">Kod parçacığı Seçici'de bulunur **Windows işletim sistemi > Windows Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="c358b-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="c358b-107">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c358b-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c358b-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c358b-108">Compiling the Code</span></span>  
 <span data-ttu-id="c358b-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c358b-109">This example requires:</span></span>  
  
-   <span data-ttu-id="c358b-110">Bir proje başvurusu System.serviceprocess.dll'ye.</span><span class="sxs-lookup"><span data-stu-id="c358b-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="c358b-111">Üye erişimi <xref:System.ServiceProcess> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c358b-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="c358b-112">Ekleme bir `Imports` üye adları kodunuzda tamamen niteleyemiyorsanız deyimi.</span><span class="sxs-lookup"><span data-stu-id="c358b-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="c358b-113">Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="c358b-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c358b-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c358b-114">Robust Programming</span></span>  
 <span data-ttu-id="c358b-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Özelliği <xref:System.ServiceProcess.ServiceController> sınıfı varsayılan olarak yerel bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="c358b-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="c358b-116">Başka bir bilgisayarda Windows Hizmetleri başvurmak için değişiklik <xref:System.ServiceProcess.ServiceController.MachineName%2A> özelliğini bilgisayarın adı.</span><span class="sxs-lookup"><span data-stu-id="c358b-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="c358b-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="c358b-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="c358b-118">Hizmet duraklatılamaz.</span><span class="sxs-lookup"><span data-stu-id="c358b-118">The service cannot be paused.</span></span> <span data-ttu-id="c358b-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="c358b-119">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="c358b-120">Bir sistem API'si erişirken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c358b-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="c358b-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="c358b-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c358b-122">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c358b-122">.NET Framework Security</span></span>  
 <span data-ttu-id="c358b-123">Bilgisayardaki hizmetlerin denetimi kullanılarak kısıtlanabilir <xref:System.ServiceProcess.ServiceControllerPermissionAccess> izinleri ayarlamak için <xref:System.ServiceProcess.ServiceControllerPermission>.</span><span class="sxs-lookup"><span data-stu-id="c358b-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="c358b-124">Kullanarak hizmet bilgilere erişimi kısıtlanabilir <xref:System.Security.Permissions.PermissionState> izinleri ayarlamak için <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="c358b-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c358b-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c358b-125">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>  
 [<span data-ttu-id="c358b-126">Nasıl Yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c358b-126">How to: Continue a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
