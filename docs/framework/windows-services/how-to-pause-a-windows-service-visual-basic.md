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
ms.openlocfilehash: 8a75c6a03f130e0a141107c81c946fc6a33b9f6c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592531"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a>Nasıl yapılır: Windows Hizmetini Duraklatma (Visual Basic)
Bu örnekte <xref:System.ServiceProcess.ServiceController> yerel bilgisayarda IIS Yönetici Hizmeti duraklatma bileşeni.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **Windows işletim sistemi > Windows Hizmetleri**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Bir proje başvurusu System.serviceprocess.dll'ye.  
  
- Üye erişimi <xref:System.ServiceProcess> ad alanı. Ekleme bir `Imports` üye adları kodunuzda tamamen niteleyemiyorsanız deyimi. Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A> Özelliği <xref:System.ServiceProcess.ServiceController> sınıfı varsayılan olarak yerel bilgisayardır. Başka bir bilgisayarda Windows Hizmetleri başvurmak için değişiklik <xref:System.ServiceProcess.ServiceController.MachineName%2A> özelliğini bilgisayarın adı.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Hizmet duraklatılamaz. (<xref:System.InvalidOperationException>)  
  
- Bir sistem API'si erişirken bir hata oluştu. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bilgisayardaki hizmetlerin denetimi kullanılarak kısıtlanabilir <xref:System.ServiceProcess.ServiceControllerPermissionAccess> izinleri ayarlamak için <xref:System.ServiceProcess.ServiceControllerPermission>.  
  
 Kullanarak hizmet bilgilere erişimi kısıtlanabilir <xref:System.Security.Permissions.PermissionState> izinleri ayarlamak için <xref:System.Security.Permissions.SecurityPermission>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [Nasıl yapılır: Bir Windows hizmeti (Visual Basic)](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
