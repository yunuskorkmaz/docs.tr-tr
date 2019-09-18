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
ms.openlocfilehash: 166eda4a9348188fa6e5048fd3ce41645cde4816
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053591"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a>Nasıl yapılır: Windows Hizmetini Duraklatma (Visual Basic)
Bu örnek, <xref:System.ServiceProcess.ServiceController> bileşeni yerel bilgisayardaki IIS Yöneticisi hizmetini duraklatmak için kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, Windows **Işletim sistemi > Windows Hizmetleri**' nde bulunur. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System. ServiceProcess. dll dosyasına bir proje başvurusu.  
  
- <xref:System.ServiceProcess> Ad alanının üyelerine erişin. Kodunuzda üye `Imports` adlarını tam olarak nitedıysanız bir ifade ekleyin. Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.ServiceProcess.ServiceController> Sınıfının özelliği, varsayılan olarak yerel bilgisayardır. <xref:System.ServiceProcess.ServiceController.MachineName%2A> Başka bir bilgisayardaki Windows hizmetlerine başvurmak için, <xref:System.ServiceProcess.ServiceController.MachineName%2A> özelliği bu bilgisayarın adıyla değiştirin.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Hizmet duraklatılamıyor. (<xref:System.InvalidOperationException>)  
  
- Sistem API 'sine erişirken bir hata oluştu. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bilgisayardaki hizmetlerin denetimi, <xref:System.ServiceProcess.ServiceControllerPermissionAccess> <xref:System.ServiceProcess.ServiceControllerPermission>içindeki izinleri ayarlamak için kullanılarak kısıtlanabilir.  
  
 Hizmet bilgilerine erişim, <xref:System.Security.Permissions.PermissionState> <xref:System.Security.Permissions.SecurityPermission>içindeki izinleri ayarlamak için kullanılarak kısıtlanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [Nasıl yapılır: Bir Windows hizmetine devam et (Visual Basic)](how-to-continue-a-windows-service-visual-basic.md)
