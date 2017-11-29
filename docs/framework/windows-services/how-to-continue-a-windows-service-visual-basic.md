---
title: "Nasıl Yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
f1_keywords: ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 28dbbf2376416a340ad7853c026b2f763f695dcb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>Nasıl Yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)
Bu örnekte <xref:System.ServiceProcess.ServiceController> IIS Yönetim hizmeti yerel bilgisayarda devam etmek için bileşen.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici bulunur **Windows işletim sistemi > Windows Hizmetleri**. Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   System.serviceprocess.dll'ye proje başvurusu.  
  
-   Üye erişimi <xref:System.ServiceProcess> ad alanı. Ekleme bir `Imports` üye adlarının kodunuzda tam olarak niteleyemiyorsanız deyimi. Daha fazla bilgi için bkz: [Imports deyimi (.NET Namespace ve türü)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A> Özelliği <xref:System.ServiceProcess.ServiceController> sınıfı varsayılan olarak yerel bilgisayardır. Başka bir bilgisayarda Windows Hizmetleri başvurmak için değiştirme <xref:System.ServiceProcess.ServiceController.MachineName%2A> o bilgisayarın adını özelliğine.  
  
 Çağıramazsınız <xref:System.ServiceProcess.ServiceController.Continue%2A> hizmet denetleyicisi durumu olana kadar bir hizmet yöntemini <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Hizmet sürdürülemez. (<xref:System.InvalidOperationException>)  
  
-   Sistem API erişirken bir hata oluştu. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bilgisayardaki hizmetlerin denetimi kullanarak kısıtlanabilir <xref:System.ServiceProcess.ServiceControllerPermissionAccess> izinleri ayarlamak için numaralandırma <xref:System.ServiceProcess.ServiceControllerPermission> sınıfı.  
  
 Kullanarak hizmet bilgilerine erişim kısıtlanabilir <xref:System.Security.Permissions.PermissionState> izinleri ayarlamak için numaralandırma <xref:System.Security.Permissions.SecurityPermission> sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [Nasıl yapılır: bir Windows hizmeti (Visual Basic) duraklatma](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
