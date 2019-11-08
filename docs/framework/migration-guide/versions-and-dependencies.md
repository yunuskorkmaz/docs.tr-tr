---
title: .NET Framework Sürümleri ve Bağımlılıkları
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: eadb456bafb1703c687e73c6aecc81c9dccae72c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739573"
---
# <a name="net-framework-versions-and-dependencies"></a>.NET Framework sürümleri ve bağımlılıklar

Her bir .NET Framework sürümü ortak dil çalışma zamanını (CLR), temel sınıf kitaplıklarını ve diğer yönetilen kitaplıkları içerir. Bu konu, sürüme göre .NET Framework'ün temel özellikleri açıklar, temel CLR sürümleri ve ilişkili geliştirme ortamları hakkında bilgi sağlar ve Windows işletim sistemi tarafından yüklenen sürümleri tanımlar.  
  
> [!NOTE]
> .NET Framework indirme ve yükleme hakkında daha fazla bilgi için bkz. [geliştiriciler için .NET Framework yükleme](../install/guide-for-developers.md).  
  
Aşağıdaki tablo .NET Framework sürüm geçmişini özetler ve her sürümü Visual Studio, Windows ve Windows Server ile ilişkilendirir. Visual Studio çoklu hedefleme sağlar, bu nedenle listelenen .NET Framework sürümüyle sınırlı değilsiniz.  
  
.NET Framework'ün her yeni sürümü önceki sürümlerdeki özellikleri korur ve yeni özellikler ekler. CLR kendi sürüm numarası ile tanımlanır. CLR sürümü her zaman artırılmamasına rağmen her sürümde, .NET Framework sürüm numarası artırılır. Örneğin, .NET Framework 4, 4,5 ve üzeri sürümlerde CLR 4, .NET Framework 2,0, 3,0 ve 3,5 de CLR 2,0 sayılabilir. (CLR'nin sürüm 3'ü yoktur.)  
  
Desteklenen işletim sistemlerinin tüm listesi için bkz. [sistem gereksinimleri](../get-started/system-requirements.md) . İndirmeler için bkz. [geliştiriciler için .NET Framework yüklemesi](../install/guide-for-developers.md). Bilgisayara hangi .NET Framework sürümlerinin yüklendiğini belirlemek için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](how-to-determine-which-versions-are-installed.md).  
  
Tabloda, ✓ ile işaretlenmiş ve **Windows 'a** dahil edilen ve Windows **Server** sütunlarında yüklü olan işletim sistemi sürümlerinde yüklü olan .NET Framework sürümleri, [denetimde etkin olmalıdır Panel](../install/dotnet-35-windows-10.md) (Windows için) veya Sunucu Yöneticisi (Windows Server için) ile etkinleştirilir.  

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]
 
|.NET Framework sürümü|CLR sürümü|Dahil edilen<br /> Visual Studio<br/>sürüm|✓<br />+ Yüklenebilir<br />Windows|✓<br />+ Yüklenebilir<br />Windows Server|Yüklü .NET sürümünü belirleme|  
|----------------------------|-----------------|--------------|---------------------------------------|----------------------------------------------------|-----------------------------------------------------------|-----------------------------------------| 
|4,8<br/><br/>[Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-48)<br/><br/>[Erişilebilirlik 'de yeni](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)<br /><br >[Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)|4| | ✓ 10 Mayıs 2019 güncelleştirmesi<br/><br/> + 10 Ekim 2018 Güncelleştirmesi (sürüm 1809) <br/> + 10 Nisan 2018 Güncelleştirmesi (sürüm 1803) <br/> + 10 Fall Creators Update (sürüm 1709) <br/> + 10 Creators Update (sürüm 1703) <br/> + 10 yıldönümü Güncelleştirmesi (sürüm 1607) <br/> + 8,1 <br/> \+ 7 | + Windows Server 2019<br/> + Windows Server, sürüm 1809 <br/> + Windows Server, sürüm 1803 <br/> + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |`Release` DWORD kullanın:<br/><br/> -528040 (Windows 10 Mayıs 2019 güncelleştirme) <br/> -528049 (diğer tüm işletim sistemi sürümleri) <br/><br/> (bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|
|4.7.2<br/><br/>[Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-472)<br/><br/>[Erişilebilirlik 'de yeni](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)<br /><br >[Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)|4| | ✓ 10 Ekim 2018 Güncelleştirmesi (sürüm 1809) <br/> ✓ 10 Nisan 2018 Güncelleştirmesi (sürüm 1803) <br/><br/> + 10 Fall Creators Update (sürüm 1709) <br/> + 10 Creators Update (sürüm 1703) <br/> + 10 yıldönümü Güncelleştirmesi (sürüm 1607) <br/> + 8,1 <br/> \+ 7 | ✓ Windows Server 2019<br/> ✓ Windows Server, sürüm 1809 <br/> ✓ Windows Server, sürüm 1803 <br/><br/> + Windows Server, sürüm 1709 <br/> + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |`Release` DWORD kullanın:<br/><br/> -461814 (Windows 10 Ekim 2018 güncelleştirmesi) <br/> -461808 (Windows 10 Nisan 2018 güncelleştirme ve Windows Server, sürüm 1803) <br/> -461814 (diğer tüm işletim sistemi sürümleri) <br/><br/> (bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|
|4.7.1<br/><br/>[Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-471)<br/><br/>[Erişilebilirlik 'de yeni](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)<br /><br >[Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)|4| | ✓ 10 Fall Creators Update (sürüm 1709) <br/> <br/> + 10 Creators Update (sürüm 1703) <br/> + 10 yıldönümü Güncelleştirmesi (sürüm 1607) <br/> + 8,1 <br/> \+ 7| + Windows Server, sürüm 1803 <br/><br/> ✓ Windows Server, sürüm 1709 <br/><br/> + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |`Release` DWORD kullanın:<br/><br/> -461308 (Windows 10 Creators Update ve Windows Server, sürüm 1709) <br/> -461310 (diğer tüm işletim sistemi sürümleri) <br/><br/> (bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))| 
|4,7<br/><br/>[Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-47)<br /><br >[Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)|4| | ✓ 10 Creators Update (sürüm 1703) <br/> <br/> + 10 yıldönümü Güncelleştirmesi (sürüm 1607) <br/> + 8,1 <br/> \+ 7| + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |`Release` DWORD kullanın:<br/><br/> -460798 (Windows 10 Creators Update) <br/> -460805 (diğer tüm işletim sistemi sürümleri) <br/><br/> (bkz. [yönergeler](how-to-determine-which-versions-are-installed.md)) |  
|4.6.2<br/><br/>[Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-462)<br /><br >[Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)|4||✓ 10 yıldönümü Güncelleştirmesi (sürüm 1607) <br /><br /> + 10 Kasım Güncelleştirmesi (sürüm 1511) <br/> + 10 <br/> + 8,1<br />+ 7|✓ 2016<br /><br /> + 2012 R2<br />+ 2012<br />+ 2008 R2 SP1|`Release` DWORD kullanın:<br /><br /> -394802 (Windows 10 yıldönümü güncelleştirmesi ve Windows Server 2016) <br />-394806 (diğer tüm işletim sistemi sürümleri)<br /><br /> (bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|  
|4.6.1<br/><br/>[Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-461)<br /><br >[Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)|4||✓ 10 Kasım Güncelleştirmesi (sürüm 1511) <br /><br /> + 10<br />+ 8,1<br />+ 8<br />+ 7|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1|`Release` DWORD kullanın:<br /><br /> -394254 (Windows 10 Kasım güncelleştirmesi)<br />-394271 (diğer tüm işletim sistemi sürümleri)<br /><br /> (bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|  
|4.6<br/><br/>[Yeni özellikler](../whats-new/index.md#whats-new-in-net-2015)<br /><br >[Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)|4|2015|✓ 10<br /><br />+ 8,1<br />+ 8<br />+ 7<br />+ Vista|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|`Release` DWORD kullanın:<br /><br /> -393295 (Windows 10)<br />-393297 (diğer tüm işletim sistemi sürümleri)<br /><br /> (bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|  
|4.5.2<br/><br/>[Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-452)<br /><br >[Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)|4|-|+ 8,1<br />+ 8<br />+ 7<br />+ Vista|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|`Release` DWORD kullanın:<br /><br /> 379893<br /><br />(bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|  
|4.5.1<br/><br/>[Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-451)<br /><br >[Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)|4|2013|✓ 8,1<br /><br />+ 8<br />+ 7<br />+ Vista|✓ 2012 R2<br /><br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|`Release` DWORD kullanın:<br /><br /> -378675 (Windows 8.1)<br />-378758 (tümü)<br /><br /> (bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|  
|4,5<br/><br/>[Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-45)<br /><br >[Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)|4|2012|✓ 8<br />+ 7<br />+ Vista|✓ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|`Release` DWORD kullanın:<br /><br /> 378389<br /><br />(bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|  
|4<br/><br/>[Yeni özellikler](../whats-new/index.md)|4|2010|+ 7<br />+ Vista|+ 2008 R2 SP1<br />+ 2008 SP2<br />+ 2003|[Yönergelere](how-to-determine-which-versions-are-installed.md) bakın|  
|3.5<br/><br/>[Yeni özellikler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\))|2,0|2008|✓ 10\*<br/>✓ 8,1\*<br />✓ 8\*<br />✓ 7<br /><br />+ Vista|  + Windows Server, sürüm 1803\* <br/> + Windows Server, sürüm 1709\* <br/> + 2016\* <br/>+ 2012 R2\*<br />+ 2012\*<br /><br />✓ 2008 R2 SP1\*<br /><br/>+ 2008 SP2<br />+ 2003|[Yönergelere](how-to-determine-which-versions-are-installed.md) bakın|  
|3.0<br/><br/>New:<br/>WPF, WCF, WF, CardSpace|2,0|-|✓ Vista|✓ 2008 R2 SP1 *<br />✓ 2008 SP2\*<br /><br />+ 2003|[Yönergelere](how-to-determine-which-versions-are-installed.md) bakın|  
|2,0<br/><br/>[Yeni özellikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/ms229284\(v%3dvs.80\))|2,0|2005|-|✓ 2008 R2 SP1<br />✓ 2008 SP2<br />✓ 2003|[Yönergelere](how-to-determine-which-versions-are-installed.md) bakın|  
|1.1<br/><br/>[Yeni özellikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/9wtde3k4\(v%3dvs.71\))|1.1|2003|-|✓ 2003|[Yönergelere](how-to-determine-which-versions-are-installed.md) bakın|  
|1.0|1.0|Visual Studio .NET|-|-|[Yönergelere](how-to-determine-which-versions-are-installed.md) bakın|  

> [!NOTE]
>
> - .NET Framework, bu işletim sisteminde [Denetim Masası (Windows için) veya Sunucu Yöneticisi (Windows Server için)](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel)üzerinden etkinleştirilmelidir.
> - Genel olarak, kullandığınız bir uygulama belirli bir sürüme bağlı olabileceği veya o sürüm kaldırılırsa bozulabileceği için bilgisayarınıza yüklü olan .NET Framework sürümlerinden hiçbirini kaldırmamanız gerekir. .NET Framework'ün birden çok sürümünü aynı anda tek bir bilgisayara yükleyebilirsiniz. Diğer bir deyişle, önceki sürümleri kaldırmak zorunda kalmadan .NET Framework yükleyebilirsiniz. Daha fazla bilgi için bkz [. Başlarken](../get-started/index.md).

## <a name="target-and-run-apps-for-version-45-and-later"></a>Sürüm 4,5 ve üzeri için uygulamaları hedefleme ve çalıştırma

.NET Framework 4,5, bilgisayarınızda .NET Framework 4 ' ü değiştiren ve benzer şekilde .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 ve 4,8, .NET Framework 4,5 için yerinde güncelleştirme, yani aynı çalışma zamanını kullandıkları anlamına gelir. , ancak derleme sürümleri güncelleştirilir ve yeni türler ve Üyeler dahil edilir. Bu güncelleştirmelerden birini yükledikten sonra, .NET Framework 4, .NET Framework 4,5, .NET Framework 4,6 veya .NET Framework 4,7 uygulamalarının yeniden derleme gerekmeden çalışmaya devam etmesi gerekir. Ancak tersi doğru değildir. .NET Framework önceki bir sürümünde .NET Framework sonraki bir sürümünü hedefleyen uygulamalar çalıştırmayı önermiyoruz. Örneğin, .NET Framework 4,5 üzerinde 4,6 .NET Framework hedeflerini bir uygulama çalıştırmanızı önermiyoruz. Aşağıdaki kurallar uygulanır:  
  
- Visual Studio 'da, proje için hedef çerçeve olarak .NET Framework 4,5 ' ı seçebilirsiniz (Bu, <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType> özelliğini ayarlar), projeyi bir .NET Framework 4,5 derlemesi veya çalıştırılabilir olarak derlemek için kullanabilirsiniz. Bu derleme veya yürütülebilir dosya .NET Framework 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 veya 4,8 yüklü herhangi bir bilgisayarda kullanılabilir.  
  
- Visual Studio 'da, bir projenin .NET Framework 4.5.1 derlemesi veya çalıştırılabilir olarak derlenmesi için hedef Framework olarak .NET Framework 4.5.1 seçebilirsiniz. Bu derlemeyi veya yürütülebilir dosyayı yalnızca .NET Framework 4.5.1 veya üzeri yüklü bilgisayarlarda çalıştırın. .NET Framework 4.5.1 hedefleyen bir yürütülebilir dosya, yalnızca .NET Framework .NET Framework 4,5 gibi önceki bir sürümü olan bir bilgisayarda çalışır. Kullanıcıdan .NET Framework 4.5.1 yüklemesi istenir. Ayrıca, .NET Framework 4.5.1 derlemeleri .NET Framework önceki bir sürümünü (.NET Framework 4,5 gibi) hedefleyen bir uygulamadan çağrılmamalıdır.  
  
  > [!NOTE]
  > .NET Framework 4.5.1 ve .NET Framework 4,5 burada yalnızca örnek olarak kullanılır. Açıklanan ilke, üzerinde çalıştığı sistemde yüklü olandan daha sonraki bir sürümü .NET Framework hedefleyen tüm uygulamalar için geçerlidir.  
  
.NET Framework bazı değişiklikler uygulama kodunuzda değişiklik yapılmasını gerektirebilir. .NET Framework 4,5 veya sonraki sürümlerde mevcut bir uygulamayı çalıştırıyorsanız, bkz. [uygulama uyumluluğu](application-compatibility.md). Geçerli sürümü yükleme hakkında daha fazla bilgi için bkz. [geliştiriciler için .NET Framework yükleme](../install/guide-for-developers.md). .NET Framework için destek hakkında daha fazla bilgi için Microsoft Desteği Web sitesindeki [Microsoft .NET Framework destek yaşam döngüsü ilkesi](https://support.microsoft.com/help/17455/lifecycle-faq-net-framework) ' ne bakın.  
  
## <a name="target-and-run-apps-for-older-versions"></a>Daha eski sürümler için uygulamaları hedefleme ve çalıştırma  

2,0, 3,0 ve 3,5 .NET Framework sürümleri CLR 'nin aynı sürümüyle (CLR 2,0) oluşturulmuştur. Bu sürümler, tek bir kurulumun ardışık katmanlarını temsil eder. Her sürüm kademeli olarak önceki sürümlerin üzerine yerleştirilir. 2,0, 3,0 ve 3,5 sürümlerini bir bilgisayar üzerinde yan yana çalıştırmak mümkün değildir. Sürüm 3.5'i yüklediğinizde, 2.0 ve 3.0 katmanlarını otomatik olarak alırsınız ve 2.0, 3.0 ve 3.5 sürümleri için oluşturulmuş olan uygulamaların tümü 3.5 sürümü üzerinde çalıştırılabilir. Ancak, .NET Framework 4 Bu katmanlama yaklaşımını sonlandırır ve bu ve sonraki sürümleri (.NET Framework 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 ve 4,8), tek bir yüklemenin birbirini izleyen katmanlarını da temsil eder. .NET Framework 4 ' te başlayarak, tek bir işlemde CLR 'nin birden çok sürümünü çalıştırmak için işlem içi, yan yana barındırma kullanabilirsiniz. Daha fazla bilgi için bkz. [derlemeler ve yan yana yürütme](../../standard/assembly/side-by-side-execution.md).  
  
Ayrıca, uygulamanız 2,0, 3,0 veya 3,5 sürümünü hedefliyorsa, kullanıcılarınız uygulamanızı çalıştırmadan önce Windows 8, Windows 8.1 veya Windows 10 bilgisayarında .NET Framework 3,5 ' i etkinleştirmek zorunda kalabilir. Daha fazla bilgi için bkz. [Windows 10, Windows 8.1 ve Windows 8 ' de .NET Framework 3,5](../install/dotnet-35-windows-10.md)'yi.  
  
## <a name="next-steps"></a>Sonraki adımlar  
  
- .NET Framework yeni başladıysanız, önemli kavramlara ve özelliklere giriş için [genel bakış](../get-started/overview.md) bölümüne bakın.  
  
- .NET Framework 4,5 ve noktası sürümlerindeki yeni özellikler ve geliştirmeler için bkz. [.NET Framework](../whats-new/index.md)yenilikler.  
  
- Uygulamanızı .NET Framework daha yeni bir sürüme geçirme hakkında daha fazla bilgi için, bkz. [Geçiş Kılavuzu](index.md).
  
- Bir bilgisayarda hangi sürümlerin veya güncelleştirmelerin yüklü olduğunu belirleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](how-to-determine-which-versions-are-installed.md) ve [nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini](how-to-determine-which-net-framework-updates-are-installed.md)belirleme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sürüm uyumluluğu](version-compatibility.md)
- [Microsoft .NET Framework destek yaşam döngüsü ilkesi](https://support.microsoft.com/help/17455/lifecycle-faq-net-framework)
- [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](../install/troubleshoot-blocked-installations-and-uninstallations.md)
