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
ms.openlocfilehash: 0b95bab20299b966b9f3c6e6ce089a641670f974
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933409"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Bir Windows Formunda bir ActiveX Denetimi Barındırmayla İlgili Konular
Windows Forms Windows Forms denetimleri barındırmak için iyileştirildi olsa da, ActiveX denetimlerini kullanmaya devam edebilirsiniz. ActiveX denetimlerini kullanan bir uygulamayı planlarken aşağıdaki noktaları göz önünde bulundurun:  
  
- **Güvenlik** Ortak dil çalışma zamanı, kod erişim güvenliği ile ilgili olarak geliştirilmiştir. Windows Forms sahip uygulamalar, tamamen güvenilir bir ortamda sorun olmadan ve kısmen güvenilir bir ortamda, işlevselliğin çoğuna erişilebilen uygulamalar çalıştırabilir. Windows Forms denetimleri, bir tarayıcıda barındırılabilecek ve hiçbir zorluk olmadan barındırılabilir. Ancak Windows Forms ActiveX denetimleri bu güvenlik geliştirmelerinden yararlanamaz. Bir ActiveX denetimi çalıştırmak, <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> özelliği ile ayarlanan, yönetilmeyen kod iznini gerektirir. Güvenlik ve yönetilmeyen kod izni hakkında daha fazla bilgi için bkz <xref:System.Security.Permissions.SecurityPermissionAttribute>.  
  
- **Toplam sahip olma maliyeti** Bir Windows formuna eklenen ActiveX denetimleri, bu Windows formuyla tamamen dağıtılır ve bu, oluşturulan dosya (ler) in boyutuna önemli ölçüde eklenebilir. Ayrıca, Windows Forms üzerinde ActiveX denetimlerinin kullanılması, kayıt defterine yazmayı gerektirir. Bu, bir kullanıcının bilgisayarına Windows Forms kontrollerine göre daha fazla inildir ve bunu gerektirmez.  
  
    > [!NOTE]
    > Bir ActiveX denetimiyle çalışmak için COM birlikte çalışma sarmalayıcısı kullanılması gerekir. Daha fazla bilgi için bkz. [Visual Basic ve görselde C#com birlikte çalışabilirliği ](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
    > [!NOTE]
    > ActiveX denetiminin bir üyesinin adı .NET Framework tanımlı bir adla eşleşiyorsa, ActiveX denetimi İçeri Aktarıcı, <xref:System.Windows.Forms.AxHost> türetilmiş sınıfı oluşturduğunda, üye adının **CTL** ile ön ekine sahip olur. Örneğin, ActiveX denetiminizin **Düzen**adlı bir üyesi varsa, **Düzen** olayı .NET Framework içinde tanımlandığından AxHost ile türetilmiş sınıfta **CtlLayout** olarak yeniden adlandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Forms için ActiveX denetimleri ekleme](how-to-add-activex-controls-to-windows-forms.md)
- [Kod erişim güvenliği](../../misc/code-access-security.md)
- [Çeşitli dillerde ve kitaplıklarda karşılaştırılan denetimler ve programlanabilir nesneler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Windows Forms’a Denetimler Yerleştirme](putting-controls-on-windows-forms.md)
- [Windows Forms Denetimleri](index.md)
