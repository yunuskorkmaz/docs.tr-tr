---
title: .NET Framework Araçları
ms.date: 03/30/2017
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81110736651db9fe00b116c3abbbdaa8d3670bee
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456103"
---
# <a name="net-framework-tools"></a>.NET Framework Araçları
.NET Framework araçları, .NET Framework'ü hedefleyen uygulamaları ve bileşenleri oluşturmayı, dağıtmayı ve yönetmeyi kolaylaştırmayı sağlar.  
  
Bu bölümde açıklanan .NET Framework Araçlarının çoğu Visual Studio ile otomatik olarak yüklenir. Visual Studio'yu indirmek için şurayı ziyaret edin [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) sayfası.
  
 Derleme Önbelleği Görüntüleyicisi (Shfusion.dll) dışında komut satırından tüm araçları çalıştırabilirsiniz. Dosya Gezgini'nde Shfusion.dll'ye erişmeniz gerekir.  
  
 Komut satırı araçlarını çalıştırmanın en iyi yolu, Visual Studio için Geliştirici Komut İstemini kullanmaktır. Bu yardımcı programlar, yükleme klasörüne gitmeden araçları kolayca çalıştırmanıza olanak sağlar. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Bazı araçlar, 32-bit bilgisayarlar veya 64-bit bilgisayarlar için özeldir. Bilgisayarınız için aracın uygun sürümünü çalıştırdığınızdan emin olun.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 Modüller ya da kaynak dosyalarından derleme bildirimi içeren bir dosya oluşturur.  
  
 [Aximp.exe (Windows Forms ActiveX Denetim İçeri Aktarıcı)](../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)  
 Bir ActiveX denetimi için bir COM tür kitaplığındaki tür tanımlarını bir Windows Forms denetimine dönüştürür.  
  
 [Caspol.exe (Kod Erişimi Güvenliği İlke Aracı)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)  
 Makine ilke düzeyi, kullanıcı ilke düzeyi ve kurumsal ilke düzeyi için güvenlik ilkesi görüntülemenize ve yapılandırmanıza olanak tanır. İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ve daha sonra bu araç kod erişim güvenliği (CAS) ilkesini etkilemez [ \<legacyCasPolicy > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) ayarlanır `true`. Daha fazla bilgi için [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
 [Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)](../../../docs/framework/tools/cert2spc-exe-software-publisher-certificate-test-tool.md)  
 Bir veya daha fazla X.509 sertifikasından bir Yazılım Yayımcıları Sertifikası (SPC) oluşturur. Bu araç yalnızca test içindir.  
  
 [Certmgr.exe (Sertifika Yönetim Aracı)](../../../docs/framework/tools/certmgr-exe-certificate-manager-tool.md)  
 Sertifikaları, sertifika güven listelerini (CTL) ve sertifika çağırma listelerini (CRL) yönetir.  
  
 [Clrver.exe (CLR Sürüm Aracı)](../../../docs/framework/tools/clrver-exe-clr-version-tool.md)  
 bilgisayarda ortak dil çalışma zamanı (CLR) yüklü tüm sürümlerini bildirir.  
  
 [CorFlags.exe (CorFlags Dönüştürme Aracı)](../../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md)  
 Taşınabilir çalıştırılabilir (PE) görüntüsünün üstbilgisine ait CorFlags bölümünü yapılandırmanıza olanak sağlar.  
  
 [Fuslogvw.exe (Bütünleştirilmiş Kod Bağlaması Günlük Görüntüleyici)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md)  
 Derleme hakkında, .NET Framework'ün çalışma zamanında neden derlemeyi bulamadığını tanılamanıza yardımcı olacak bilgiler görüntüler.  
  
 [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 Genel derleme önbelleğinin içeriğini görüntülemenize, kullanmanıza ve önbelleği indirmenize olanak sağlar.  
  
 [Ilasm.exe (IL Derleyici)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)  
 Ara dil'den (IL) taşınabilir çalıştırılabilir bir (PE) dosya oluşturur. IL'in beklendiği gibi çalışıp çalışmadığını belirlemek için elde edilen çalıştırılabilir dosyayı çalıştırabilirsiniz.  
  
 [Ildasm.exe (IL Ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
 Ara dil (IL) kodunu içeren taşınabilir, çalıştırılabilir (PE) dosyayı alır ve IL Derleyicisi'ne (Ilasm.exe) girdi olmaya uygun bir metin dosyası oluşturur.  
  
 [Installutil.exe (Yükleme Aracı)](../../../docs/framework/tools/installutil-exe-installer-tool.md)  
 Belirtilen bir derlemedeki yükleyici bileşenlerini yürüterek sunucu kaynaklarını yüklemenize ve kaldırmanıza olanak verir. (Alanındaki sınıflarla çalışır <xref:System.Configuration.Install> ad.) 
  
 [Lc.exe (Lisans Derleyici)](../../../docs/framework/tools/lc-exe-license-compiler.md)  
 Lisans bilgilerini içeren metin dosyalarını okur ve kaynak olarak bir ortak dil çalışma zamanı çalıştırılabilir dosyasının içinde katıştırılabilir bir .licenses dosyası oluşturur. 
  
 [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 Uygulama ve dağıtım bildirimleri oluşturmanıza, düzenlemenize ve imzalamanıza olanak verir. Bir komut satırı aracı olarak Mage.exe, hem toplu betiklerden hem de ASP.NET uygulamaları dahil diğer Windows tabanlı uygulamalardan çalıştırılabilir.  
  
 [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
 Komut satırı aracı Mage.exe ile aynı işlevselliği destekler, ancak Windows tabanlı bir kullanıcı arabirimi (UI) kullanır. Komut satırı aracı Mage.exe ile aynı işlevselliği destekler, ancak Windows tabanlı bir kullanıcı arabirimi (UI) kullanır.  
  
 [MDbg.exe (.NET Framework Komut Satırı Hata Ayıklayıcı)](../../../docs/framework/tools/mdbg-exe.md)  
 Araç satıcılarının ve uygulama geliştiricilerin, .NET Framework ortak dil çalışma zamanını hedefleyen programlardaki hataları bulmalarına ve düzeltmelerine yardımcı olur. Bu araç, hata ayıklama hizmetleri sağlamak için çalışma zamanı hata ayıklama API kullanır.  
  
 [Mgmtclassgen.exe (Yönetim Türü Kesin Belirlenmiş Sınıf Oluşturucu)](../../../docs/framework/tools/mgmtclassgen-exe.md)  
 Belirtilen bir Windows Yönetim Araçları (WMI) sınıfı için bir erken bağlanan bir yönetilen sınıf oluşturmanıza olanak sağlar.  
  
 [Mpgo.exe (Yönetilen Profil Temelli İyileştirme Aracı)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md)  
 Yaygın son kullanıcı senaryolarını kullanarak yerel görüntü derlemelerini ayarlamanıza olanak verir. Mpgo.exe, uygulama geliştiricisi tarafından seçilen eğitim senaryolarını kullanarak yerel görüntü uygulama derlemeleri (.NET Framework derlemeleri değil) için profil verileri oluşturmasına ve bunların kullanılmasına olanak verir.  
  
 [Ngen.exe (Yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)  
 Yerel görüntüler (işlemciye özel derlenmiş makine kodu içeren dosyalar) kullanarak yönetilen uygulamaların performansını artırır. Çalışma zamanı orijinal derlemeyi derlemek için anlık (JIT) derleyiciyi kullanmak yerine önbellekteki yerel görüntüleri kullanabilir.  
  
 [Peverify.exe (PEVerify Aracı)](../../../docs/framework/tools/peverify-exe-peverify-tool.md)  
 Microsoft ara dil (MSIL) kodunuzun ve ilişkili meta verilerinizin tür güvenlik gereksinimlerini karşılamasına yardımcı olur. Microsoft ara dil (MSIL) kodunuzun ve ilişkili meta verilerinizin tür güvenlik gereksinimlerini karşılamasına yardımcı olur.  
  
 [Regasm.exe (Derleme Kayıt Aracı)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)  
 Bir derleme içindeki meta veriyi okur ve gerekli girişleri kayıt defterine ekler. Bu, COM istemcilerinin .NET Framework sınıfları olarak görünmesini sağlar.  
  
 [Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md)  
 Bir derlemeyi yükler ve kaydettirir, bir tür kitaplığı oluşturur ve belirtilen bir COM+ sürümü 1.0 uygulamasına yükler, bir sınıfa programlı şekilde eklediğiniz hizmetleri yapılandırır.  
  
 [Resgen.exe (Kaynak Dosya Oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 Metin (.txt veya .restext) dosyalarını ve XML tabanlı kaynak biçimi (.resx) dosyalarını, bir çalışma zamanı ikili çalıştırılabilir dosyasına katıştırılabilen veya uydu derlemeleri haline getirilebilen ortak dil çalışma zamanı ikili (.resources) dosyalarına dönüştürür.  
  
 [SecAnnotate.exe (.NET Güvenlik Not Ekleyici Aracı)](../../../docs/framework/tools/secannotate-exe-net-security-annotator-tool.md)  
 Bir derlemeyi SecurityCritical ve SecuritySafeCritical bölümlerini tanımlar. Tanımlar `SecurityCritical` ve `SecuritySafeCritical` bölümlerini derleme.  
  
 [SignTool.exe (İmza Aracı)](../../../docs/framework/tools/signtool-exe.md)  
 Dosyaları dijital olarak imzalar, dosyalardaki imzaları doğrular ve dosyalara zaman damgası ekler.  
  
 [Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 Derlemelerin tanımlayıcı adlarla oluşturulmasına yardımcı olur. Bu araç, temel yönetim, imza oluşturma ve imza doğrulaması için seçenekler sağlar.  
  
 [SOS.dll (SOS Hata Ayıklama Uzantısı)](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md)  
 İç ortak dil çalışma zamanı (CLR) ortamıyla ilgili bilgi sağlayarak, WinDbg.exe hata ayıklayıcısındaki ve Visual Studio'daki yönetilen programlarda hata ayıklamanıza yardımcı olur.  
  
 [SqlMetal.exe (Kod Üretme Aracı)](../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 .NET Framework'ün LINQ-SQL bileşenine kod ve eşleme oluşturur.  
  
 [Storeadm.exe (Yalıtılmış Depolama Aracı)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md)  
 Yalıtılmış depolamayı yönetir; kullanıcının mağazalarını listeleyen ve bunları silen seçenekler sağlar.  
  
 [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 Bir ortak dil çalışma zamanı derlemesinde tanımlanan türleri açıklayan bir tür kitaplığı oluşturur.  
  
 [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 Bir COM tür kitaplığında bulunan tür tanımlarını bir ortak dil çalışma zamanı derlemesindeki eşdeğer tanımlara dönüştürür.  
  
 [Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)](../../../docs/framework/tools/winmdexp-exe-windows-runtime-metadata-export-tool.md)  
 Derlenmiş bir .NET Framework derlemesinin hem Windows çalışma zamanı meta veri ve uygulama bilgilerini içeren .winmd dosyası olarak paketlenmiş bir Windows çalışma zamanı bileşeni içine bir .winmdobj dosyası olarak dışarı aktarır.  
  
 [Winres.exe (Windows Forms Kaynak Düzenleyici)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 Windows Forms tarafından kullanılan kullanıcı arabirimi (UI) kaynaklarını (.resx veya .resources dosyaları) yerelleştirmenize yardımcı olur. Dizeleri çevirebilir ve ardından yerelleştirilmiş dizeleri içerecek şekilde denetimleri boyutlandırabilir, taşıyabilir ve gizleyebilirsiniz.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [WPF araçları](https://docs.microsoft.com/previous-versions/ms742404(v=vs.110))  
 İsXPS Conformance Aracı (isXPS.exe) ve profil oluşturma araçları performans gibi araçlar içerir.  
  
 [Windows Communication Foundation Araçları](../../../docs/framework/wcf/tools.md)  
 Windows Communication Foundation (WCF) uygulamalarını oluşturmanızı, dağıtmanızı ve yönetmenizi kolaylaştıran araçlar içerir.
