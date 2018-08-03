---
title: .NET Framework Sürümleri ve Bağımlılıkları
ms.custom: updateeachrelease
ms.date: 07/25/2018
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a80f615c94e6ccdb9e095a5e01dc8886bf05aa8
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "36208477"
---
# <a name="net-framework-versions-and-dependencies"></a>.NET Framework Sürümleri ve Bağımlılıkları
Her bir .NET Framework sürümü ortak dil çalışma zamanını (CLR), temel sınıf kitaplıklarını ve diğer yönetilen kitaplıkları içerir. Bu konu, sürüme göre .NET Framework'ün temel özellikleri açıklar, temel CLR sürümleri ve ilişkili geliştirme ortamları hakkında bilgi sağlar ve Windows işletim sistemi tarafından yüklenen sürümleri tanımlar.  
  
> [!NOTE]
>  İndiriliyor ve .NET Framework'ü yükleme hakkında daha fazla bilgi için bkz: [geliştiriciler için .NET Framework yükleme](../../../docs/framework/install/guide-for-developers.md).  
  
 Aşağıdaki tablo, .NET Framework sürüm geçmişi özetlenmiş ve her bir sürümü Visual Studio, Windows ve Windows Server ile ilişkilendirir. Visual Studio'nun, listelenen .NET Framework sürümüyle sınırlı kalmamanız için çoklu sürüm desteği sağladığını unutmayın.  
  
 .NET Framework'ün her yeni sürümü önceki sürümlerdeki özellikleri korur ve yeni özellikler ekler. CLR kendi sürüm numarası ile tanımlanır. CLR sürümü her zaman artırılmamasına rağmen her sürümde, .NET Framework sürüm numarası artırılır. Örneğin, .NET Framework 4, 4.5 ve sonraki sürümleri .NET Framework 2.0, ancak CLR 4 içerir, 3.0 ve 3.5 CLR 2.0 içerir. (CLR'nin sürüm 3'ü yoktur.)  
  
 Bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md) için desteklenen işletim sistemlerinin tam bir listesi. İndirmeler için bkz. [geliştiriciler için .NET Framework yükleme](../../../docs/framework/install/guide-for-developers.md). Hangi .NET Framework sürümleri bir bilgisayarda yüklü belirlemek için bkz: [nasıl yapılır: Determine Which .NET Framework sürümleri Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).  
  
 Tabloda, işletim sistemi sürümleri yüklü .NET Framework sürümlerini ✓ ile işaretlenen **dahil / Windows üzerinde yüklü** ve **dahil /WindowsServer'dayüklü**sütunları olmalıdır [Denetim Masası'nda etkin](../../../docs/framework/install/dotnet-35-windows-10.md) (Windows için) veya Sunucu Yöneticisi üzerinden (Windows Server'de) etkin.  
  
|.NET Framework sürümü|CLR sürümü|Dahil<br /> Visual Studio<br/>sürüm|✓ Dahil<br />+ Yüklenebilir<br />Windows|✓ Dahil<br />+ Yüklenebilir<br />Windows Server|Yüklü .NET sürümü belirlemek için|  
|----------------------------|-----------------|--------------|---------------------------------------|----------------------------------------------------|-----------------------------------------------------------|-----------------------------------------| 
|4.7.2<br/><br/>[Yeni Özellikler](../whats-new/index.md#whats-new-in-the-net-framework-472)<br/><br/>[Erişilebilirlik yenilikleri](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-the-net-framework-472)|4| |✓ 10 Nisan 2018 Güncelleştirmesi (sürüm 1803) <br/><br/> + 10 Creators Update (1709 sürümü) ayrılır. <br/> <br/> + 10 Creators Update (sürüm 1703) <br/> + 10 Yıldönümü Güncelleştirmesi (sürüm 1607) <br/> + 8.1 <br/> +7 | + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |Kullanım `Release` DWORD:<br/><br/> -461808 (Windows 10 Nisan 2018 güncelleştirmesi) <br/> -461814 (tüm diğer işletim sistemi sürümleri) <br/><br/> (bkz [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md))|
|4.7.1<br/><br/>[Yeni Özellikler](../whats-new/index.md#whats-new-in-the-net-framework-471)<br/><br/>[Erişilebilirlik yenilikleri](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-the-net-framework-471)|4| | ✓ 10 kalan Creators Update (1709 sürümü) <br/> <br/> + 10 Creators Update (sürüm 1703) <br/> + 10 Yıldönümü Güncelleştirmesi (sürüm 1607) <br/> + 8.1 <br/> +7| + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |Kullanım `Release` DWORD:<br/><br/> -461308 (Windows 10 Creators Update) <br/> -461310 (tüm diğer işletim sistemi sürümleri) <br/><br/> (bkz [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md))| 
|4.7<br/><br/>[Yeni Özellikler](../whats-new/index.md#whats-new-in-the-net-framework-47)|4| | ✓ 10 Creators Update (sürüm 1703) <br/> <br/> + 10 Yıldönümü Güncelleştirmesi (sürüm 1607) <br/> + 8.1 <br/> +7| + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |Kullanım `Release` DWORD:<br/><br/> -460798 (Windows 10 Creators Update) <br/> -460805 (tüm diğer işletim sistemi sürümleri) <br/><br/> (bkz [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)) |  
|4.6.2<br/><br/>[Yeni Özellikler](../whats-new/index.md#whats-new-in-the-net-framework-462)|4||✓ 10 Yıldönümü Güncelleştirmesi (sürüm 1607) <br /><br /> + 10 Kasım Güncelleştirmesi (sürüm 1511) <br/> + 10 <br/> + 8.1<br />+ 7|✓  2016<br /><br /> + 2012 R2<br />+ 2012<br />+ 2008 R2 SP1|Kullanım `Release` DWORD:<br /><br /> -394802 (Windows 10 Yıldönümü güncelleştirmesi)<br />-394806 (tüm diğer işletim sistemi sürümleri)<br /><br /> (bkz [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md))|  
|4.6.1<br/><br/>[Yeni Özellikler](../whats-new/index.md#whats-new-in-the-net-framework-461)|4|||✓ 10 Kasım Güncelleştirmesi (sürüm 1511) <br /><br /> + 10<br />+ 8.1<br />+ 8<br />+ 7|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1|Kullanım `Release` DWORD:<br /><br /> -394254 (Windows 10 Kasım güncelleştirmesi)<br />-394271 (tüm diğer işletim sistemi sürümleri)<br /><br /> (bkz [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md))|  
|4.6<br/><br/>[Yeni Özellikler](../whats-new/index.md#whats-new-in-net-2015)|4|2015|✓ 10<br />+ 8.1<br />+ 8<br />+ 7<br />+ Vista|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|Kullanım `Release` DWORD:<br /><br /> -393295 (Windows 10)<br />-393297 (tüm diğer işletim sistemi sürümleri)<br /><br /> (bkz [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md))|  
|4.5.2<br/><br/>[Yeni Özellikler](../whats-new/index.md#whats-new-in-the-net-framework-452)|4|-|+ 8.1<br />+ 8<br />+ 7<br />+ Vista|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|Kullanım `Release` DWORD:<br /><br /> 379893<br /><br />(bkz [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md))|  
|4.5.1<br/><br/>[Yeni Özellikler](../whats-new/index.md#whats-new-in-the-net-framework-451)|4|2013|✓ 8.1<br />+ 8<br />+ 7<br />+ Vista|✓ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|Kullanım `Release` DWORD:<br /><br /> -378675 (Windows 8.1)<br />-378758 (diğer)<br /><br /> (bkz [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md))|  
|4,5<br/><br/>[Yeni Özellikler](../whats-new/index.md#whats-new-in-the-net-framework-45)|4|2012|✓ 8<br />+ 7<br />+ Vista|✓ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|Kullanım `Release` DWORD:<br /><br /> 378389<br /><br />(bkz [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md))|  
|4<br/><br/>[Yeni Özellikler](http://msdn.microsoft.com/library/ms171868\(v=vs.100\).aspx)|4|2010|+ 7<br />+ Vista|+ 2008 R2 SP1<br />+ 2008 SP2<br />+ 2003|Bkz: [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)|  
|3.5<br/><br/>[Yeni Özellikler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\))|2,0|2008|✓ 10*<br/>✓ 8.1*<br />✓ 8\*<br />✓ 7<br />+ Vista|✓2008 R2 SP1*<br />+ 2012 R2*<br />+ 2012 *<br />+ 2008 SP2<br />+ 2003|Bkz: [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)|  
|3.0<br/><br/>New:<br/>WPF, WCF, WF, CardSpace|2,0|-|✓ Vista|✓ 2008 R2 SP1 *<br />✓ 2008 SP2\*<br />+ 2003|Bkz: [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)|  
|2,0<br/><br/>[Yeni Özellikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/ms229284\(v%3dvs.80\))|2,0|2005|-|✓ 2008 R2 SP1<br />✓ 2008 SP2<br />✓ 2003|Bkz: [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)|  
|1.1<br/><br/>[Yeni Özellikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/9wtde3k4\(v%3dvs.71\))|1.1|2003|-|✓ 2003|Bkz: [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)|  
|1.0|1.0|Visual Studio .NET|-|-|Bkz: [yönergeleri](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)|  

**Notlar**

<sup>\*</sup>&nbsp;&nbsp;.NET Framework bu işletim sistemindeki etkinleştirilmelidir [Denetim Masası'nı (Windows) veya Sunucu Yöneticisi'ni (Windows Server için)](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel).

 Genel olarak, kullandığınız bir uygulama belirli bir sürüme bağlı olabileceği veya o sürüm kaldırılırsa bozulabileceği için bilgisayarınıza yüklü olan .NET Framework sürümlerinden hiçbirini kaldırmamanız gerekir. .NET Framework'ün birden çok sürümünü aynı anda tek bir bilgisayara yükleyebilirsiniz. Başka bir deyişle, önceki sürümleri kaldırmadan .NET Framework'ü yükleyebilirsiniz. Daha fazla bilgi için [Başlarken](../../../docs/framework/get-started/index.md).

## <a name="targeting-and-running-net-framework-apps-for-version-45-and-later"></a>Hedefleme ve çalışan .NET Framework uygulamaları için sürüm 4.5 ve üzeri  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Yerini alan bir yerinde güncelleştirmedir [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] bilgisayarınız ve .NET Framework 4.5.1 üzerinde benzer şekilde, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 ve 4.7.2 yerinde güncelleştirmelerdir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], yani aynı kullanın, çalışma zamanı sürümü, ancak derleme sürümlerini güncelleştirilir ve yeni türleri ve üyeleri içerir. Bu güncelleştirmeler birini yükledikten sonra [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], .NET Framework 4.6 veya .NET Framework 4.7 uygulamalarını yeniden derleme gerek kalmadan çalışmaya devam etmesi gerekir. Ancak tersi doğru değildir. .NET Framework'ün önceki bir sürümünde .NET Framework'ün sonraki bir sürümünü'ı hedefleyen uygulamaların çalıştırılmasını önermiyoruz. Bir uygulama hedefleri çalıştırın, önermiyoruz [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] üzerinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Aşağıdaki kurallar uygulanır:  
  
-   Visual Studio'da seçtiğiniz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] bir projenin hedef çerçevesi (Bu ayarlar <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType> özelliği) olarak Projeyi derlemek için bir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] derleme veya yürütülebilir öğe. Bu derleme veya yürütülebilir öğe olan herhangi bir bilgisayarda sonra kullanılabilir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 veya 4.7.2 yüklü.  
  
-   Visual Studio'da seçtiğiniz [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] bir projenin hedef çerçevesi (Bu ayarlar <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType> özelliği) olarak Projeyi derlemek için bir [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] derleme veya yürütülebilir öğe. Bu derleme veya yürütülebilir öğe olan bilgisayarlarda çalıştırılması gereken [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] veya sonraki bir sürüm yüklü .NET Framework'ün. Hedefleyen yürütülebilir dosyanın [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] yalnızca .NET Framework'ün önceki bir sürümü gibi sahip bir bilgisayarda çalışması engellenir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], yüklü ve kullanıcı yüklemeniz istenir [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]. Ayrıca, [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] derlemeleri gibi .NET Framework'ün önceki bir sürümünü hedefleyen bir uygulamasından çağırılmalıdır [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
     [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] Ve [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] kullanılan örnekler olarak yalnızca burada. Bu ilke, sonraki bir sürümse .NET Framework'ün üzerinde çalıştığı için sistemde yüklü bir hedefleyen herhangi bir uygulama için geçerlidir.  
  
 .NET Framework'teki bazı değişiklikler uygulama kodunuzda değişiklikler gerektirebilir; bkz: [uygulama uyumluluğu](../../../docs/framework/migration-guide/application-compatibility.md) mevcut uygulamalarınızı çalıştırmadan önce [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya sonraki sürümler. Güncel sürümü yükleme hakkında daha fazla bilgi için bkz. [geliştiriciler için .NET Framework yükleme](../../../docs/framework/install/guide-for-developers.md). .NET Framework desteği hakkında daha fazla bilgi için bkz: [Microsoft .NET Framework desteği yaşam döngüsü ilkesi](http://go.microsoft.com/fwlink/?LinkId=196607) Microsoft Support Web sitesi.  
  
## <a name="targeting-and-running-apps-for-older-versions"></a>Daha eski sürümler için uygulamalar hedefleme ve çalıştırma  
 .NET Framework 2.0, 3.0 ve 3.5 sürümleri, aynı CLR sürümü (CLR 2.0) ile oluşturulmuştur. Bu sürümler, tek bir kurulumun ardışık katmanlarını temsil eder. Her sürüm kademeli olarak önceki sürümlerin üzerine yerleştirilir. 2.0, 3.0 ve 3.5 sürümlerini bir bilgisayar üzerinde yan yana çalıştırmak mümkün değildir. Sürüm 3.5'i yüklediğinizde, 2.0 ve 3.0 katmanlarını otomatik olarak alırsınız ve 2.0, 3.0 ve 3.5 sürümleri için oluşturulmuş olan uygulamaların tümü 3.5 sürümü üzerinde çalıştırılabilir. Ancak, .NET Framework 4 bu katmanlama yaklaşımını sona erer ve de ve sonraki sürümleri (.NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 ve 4.7.2) tek bir kurulumun ardışık katmanlarını temsil eder.  CLR'nin birden çok sürümünü tek bir işlemde çalıştırmak için, .NET Framework 4 ile başlayarak işlem içi yan yana barındırma kullanabilirsiniz. Daha fazla bilgi için [derlemeler ve yan yana yürütme](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md).  
  
 Ayrıca, uygulamanızı çalıştırabilirsiniz 2.0, 3.0 veya 3.5, kullanıcılarınızın uygulama hedef sürümü, önce bir Windows 8, Windows 8.1 veya Windows 10 bilgisayarda .NET Framework 3.5 etkinleştirmek için gerekli. Daha fazla bilgi için [Windows 10, Windows 8.1 ve Windows 8 üzerinde .NET Framework 3.5 yükleme](../../../docs/framework/install/dotnet-35-windows-10.md).  
  
## <a name="next-steps"></a>Sonraki adımlar  
  
-   .NET Framework konusunda yeniyseniz, bkz. [genel bakış](../../../docs/framework/get-started/overview.md) temel kavramlara ve özelliklere giriş için.  
  
-   İçerisindeki yeni özellikler ve geliştirmeler için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve nokta sürümlerini için bkz [.NET Framework'teki yenilikler](../../../docs/framework/whats-new/index.md).  
  
-   Uygulamanızı .NET Framework 4'e geçiş hakkında bilgi için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve nokta sürümlerini için bkz [Geçiş Kılavuzu](../../../docs/framework/migration-guide/index.md).  
  
-   Bir bilgisayarda hangi sürümlerin veya güncelleştirmelerin yüklü olduğunu belirleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Determine Which .NET Framework sürümleri Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) ve [nasıl yapılır: belirlemek, .NET Framework güncelleştirmelerin Yüklü](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

[Sürüm uyumluluğu](../../../docs/framework/migration-guide/version-compatibility.md)   
[Microsoft .NET Framework Destek Ömrü İlkesi](http://go.microsoft.com/fwlink/?LinkId=196607)   
[Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
