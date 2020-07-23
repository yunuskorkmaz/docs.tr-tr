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
# <a name="how-to-pause-a-windows-service-visual-basic"></a>Nasıl yapılır: Windows Hizmetini Duraklatma (Visual Basic)
Bu örnek, <xref:System.ServiceProcess.ServiceController> bileşeni yerel BILGISAYARDAKI IIS Yöneticisi hizmetini duraklatmak için kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, Windows **Işletim sistemi > Windows Hizmetleri**' nde bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System.serviceprocess.dll bir proje başvurusu.  
  
- <xref:System.ServiceProcess>Ad alanının üyelerine erişin. `Imports`Kodunuzda üye adlarını tam olarak nitedıysanız bir ifade ekleyin. Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A>Sınıfının özelliği, <xref:System.ServiceProcess.ServiceController> Varsayılan olarak yerel bilgisayardır. Başka bir bilgisayardaki Windows hizmetlerine başvurmak için, <xref:System.ServiceProcess.ServiceController.MachineName%2A> özelliği bu bilgisayarın adıyla değiştirin.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Hizmet duraklatılamıyor. (<xref:System.InvalidOperationException>)  
  
- Sistem API 'sine erişirken bir hata oluştu. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bilgisayardaki hizmetlerin denetimi, <xref:System.ServiceProcess.ServiceControllerPermissionAccess> içindeki izinleri ayarlamak için kullanılarak kısıtlanabilir <xref:System.ServiceProcess.ServiceControllerPermission> .  
  
 Hizmet bilgilerine erişim, <xref:System.Security.Permissions.PermissionState> içindeki izinleri ayarlamak için kullanılarak kısıtlanabilir <xref:System.Security.Permissions.SecurityPermission> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [Nasıl yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)](how-to-continue-a-windows-service-visual-basic.md)
