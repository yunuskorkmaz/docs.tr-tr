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
ms.openlocfilehash: 354c524924794cd240a230e325a4f0eee58cdc50
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705213"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Bir Windows Formunda bir ActiveX Denetimi Barındırmayla İlgili Konular
Windows Forms ana bilgisayar Windows Forms denetimleri için optimize edilmiştir ancak ActiveX denetimlerini kullanmaya devam edebilirsiniz. ActiveX denetimlerini kullanan bir uygulamayı planlarken, aşağıdaki konuları göz önünde bulundurun:  
  
-   **Güvenlik** ortak dil çalışma zamanı kod erişim güvenliği ile ilgili olarak geliştirilmiştir. Windows Forms özelliklerine sahip uygulamalar ile erişilebilir işlevselliğinin büyük sorun olmadan tam olarak güvenilen bir ortamda ve yarı güvenilir bir ortamda çalıştırabilirsiniz. Windows Forms denetimleri, hiçbir zorluklar ile bir tarayıcıda barındırılabilir. Ancak, Windows Forms ActiveX denetimlerinde bu güvenlik geliştirmeleri yararlanamaz. Bir ActiveX denetimi çalışıyor ile ayarlanan yönetilmeyen kod iznini gerektirir <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> özelliği. Güvenlik ve yönetilmeyen kod iznini hakkında daha fazla bilgi için bkz: <xref:System.Security.Permissions.SecurityPermissionAttribute>.  
  
-   **Toplam sahip olma maliyetini** bir Windows forma eklenen ActiveX denetimleri, oluşturulan dosyaların boyutunu önemli ölçüde ekleyebilirsiniz bağlandığında, Windows Form dağıtılır. Ayrıca, Windows Forms ActiveX denetimleri kullanarak, kayıt defterine yazma gerektirir. Bu gerektirmeyen Windows Forms denetimleri, bir kullanıcının bilgisayarına daha bozucu budur.  
  
    > [!NOTE]
    >  ActiveX çalışma denetimi bir COM birlikte çalışma sarmalayıcısı kullanımı gerektirir. Daha fazla bilgi için [Visual Basic ve Visual C# COM birlikte çalışabilirlik](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
    > [!NOTE]
    >  ActiveX denetiminin bir üyesinin adı içinde tanımlanan bir adla eşleşirse [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ActiveX denetim içeri Aktarıcı üye adı ile ön ek sonra **Ctl** oluşturduğunda, <xref:System.Windows.Forms.AxHost> türetilmiş sınıf. Örneğin, ActiveX denetiminizin adlı bir üyesi varsa **Düzen**, yeniden adlandırıldığında **CtlLayout** AxHost türetilen sınıfında çünkü **Düzen** olay içinde tanımlanmıştır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Windows Forms'a ActiveX denetimleri ekleme](how-to-add-activex-controls-to-windows-forms.md)
- [Kod erişimi güvenliği](../../misc/code-access-security.md)
- [Denetimler ve programlanabilir nesneler çeşitli dillerde ve kitaplıklarda karşılaştırılan](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Windows Forms’a Denetimler Yerleştirme](putting-controls-on-windows-forms.md)
- [Windows Forms Denetimleri](index.md)
