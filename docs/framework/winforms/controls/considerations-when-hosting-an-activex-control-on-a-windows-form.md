---
title: "Bir Windows Formunda bir ActiveX Denetimi Barındırmayla İlgili Konular"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ec828ca0b2bd8231d0baca72bf97bef566f2651
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Bir Windows Formunda bir ActiveX Denetimi Barındırmayla İlgili Konular
Windows Forms ana bilgisayar Windows Forms denetimleri için optimize edilmiştir rağmen ActiveX denetimlerini kullanmaya devam edebilirsiniz. ActiveX denetimleri kullanan bir uygulamayı planlarken aşağıdaki noktaları göz önünde bulundurun:  
  
-   **Güvenlik** ortak dil çalışma zamanı kod erişim güvenliği açısından geliştirilmiştir. Windows Forms özelliklerine sahip uygulamaları işlevselliğinin büyük kısmını erişilebilir ile sorun olmadan tam güvenilen bir ortamda ve yarı güvenilir bir ortamda çalıştırılabilir. Windows Forms denetimleri hiçbir zorluklar sahip tarayıcıda barındırılabilir. Ancak, Windows Forms ActiveX denetimlerinde bu güvenlik geliştirmeleri yararlanamaz. Bir ActiveX denetimini çalıştırmak ile ayarlamak yönetilmeyen kod izni gerektirir <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> özelliği. Güvenlik ve yönetilmeyen kod izin hakkında daha fazla bilgi için bkz: <xref:System.Security.Permissions.SecurityPermissionAttribute>.  
  
-   **Toplam sahip olma maliyetini** ActiveX denetimleri için Windows formu eklenen oluşturulan dosya boyutunu önemli ölçüde ekleyebilirsiniz bağlandığında bu Windows Form ile dağıtılır. Ayrıca, Windows formlarına ActiveX denetimlerini kullanarak kayıt defterine yazılıyor gerektirir. Bu gerektirmeyen Windows Forms denetimleri, bir kullanıcının bilgisayarına daha bozucu budur.  
  
    > [!NOTE]
    >  ActiveX ile çalışma denetimi COM birlikte çalışma sarmalayıcısı kullanılmasını gerektirir. Daha fazla bilgi için bkz: [COM birlikte çalışabilirliği Visual Basic ve Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
    > [!NOTE]
    >  ActiveX denetiminin üyenin adını tanımlanan bir ad eşleşirse [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ActiveX denetim içeri Aktarıcı ile üye adı ön eki sonra **Ctl** oluşturduğunda, <xref:System.Windows.Forms.AxHost> türetilmiş sınıf. ActiveX denetimi adlı bir üye varsa, örneğin, **düzeni**, yeniden adlandırılır **CtlLayout** AxHost türetilmiş sınıfında çünkü **düzeni** olay içinde tanımlanmıştır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows formlarına ActiveX denetimleri ekleme](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [Kod erişimi güvenliği](../../../../docs/framework/misc/code-access-security.md)  
 [Denetimleri ve çeşitli diller ve kitaplıkları karşılaştırıldığında programlanabilir nesneleri](http://msdn.microsoft.com/en-us/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [Windows formlarına denetimler koyma](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [Windows Forms denetimleri](../../../../docs/framework/winforms/controls/index.md)
