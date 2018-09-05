---
title: Bir Windows Formunda bir ActiveX Denetimi Barındırmayla İlgili Konular
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
ms.openlocfilehash: ebf856078d24ef44ca0e04955e0a971de68bb3ce
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512979"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Bir Windows Formunda bir ActiveX Denetimi Barındırmayla İlgili Konular
Windows Forms ana bilgisayar Windows Forms denetimleri için optimize edilmiştir ancak ActiveX denetimlerini kullanmaya devam edebilirsiniz. ActiveX denetimlerini kullanan bir uygulamayı planlarken, aşağıdaki konuları göz önünde bulundurun:  
  
-   **Güvenlik** ortak dil çalışma zamanı kod erişim güvenliği ile ilgili olarak geliştirilmiştir. Windows Forms özelliklerine sahip uygulamalar ile erişilebilir işlevselliğinin büyük sorun olmadan tam olarak güvenilen bir ortamda ve yarı güvenilir bir ortamda çalıştırabilirsiniz. Windows Forms denetimleri, hiçbir zorluklar ile bir tarayıcıda barındırılabilir. Ancak, Windows Forms ActiveX denetimlerinde bu güvenlik geliştirmeleri yararlanamaz. Bir ActiveX denetimi çalışıyor ile ayarlanan yönetilmeyen kod iznini gerektirir <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> özelliği. Güvenlik ve yönetilmeyen kod iznini hakkında daha fazla bilgi için bkz: <xref:System.Security.Permissions.SecurityPermissionAttribute>.  
  
-   **Toplam sahip olma maliyetini** bir Windows forma eklenen ActiveX denetimleri, oluşturulan dosyaların boyutunu önemli ölçüde ekleyebilirsiniz bağlandığında, Windows Form dağıtılır. Ayrıca, Windows Forms ActiveX denetimleri kullanarak, kayıt defterine yazma gerektirir. Bu gerektirmeyen Windows Forms denetimleri, bir kullanıcının bilgisayarına daha bozucu budur.  
  
    > [!NOTE]
    >  ActiveX çalışma denetimi bir COM birlikte çalışma sarmalayıcısı kullanımı gerektirir. Daha fazla bilgi için [Visual Basic ve Visual C# COM birlikte çalışabilirlik](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
    > [!NOTE]
    >  ActiveX denetiminin bir üyesinin adı içinde tanımlanan bir adla eşleşirse [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ActiveX denetim içeri Aktarıcı üye adı ile ön ek sonra **Ctl** oluşturduğunda, <xref:System.Windows.Forms.AxHost> türetilmiş sınıf. Örneğin, ActiveX denetiminizin adlı bir üyesi varsa **Düzen**, yeniden adlandırıldığında **CtlLayout** AxHost türetilen sınıfında çünkü **Düzen** olay içinde tanımlanmıştır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows Forms’a ActiveX Denetimleri Ekleme](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [Kod erişimi güvenliği](../../../../docs/framework/misc/code-access-security.md)  
 [Denetimler ve programlanabilir nesneler çeşitli dillerde ve kitaplıklarda karşılaştırılan](https://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [Windows Forms’a Denetimler Yerleştirme](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/index.md)
