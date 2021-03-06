---
title: .NET Framework araçları
description: .NET ' i hedefleyen uygulamalar ve bileşenler oluşturmanızı, dağıtmanızı ve yönetmenizi kolaylaştıran .NET araçları listesini inceleyin.
ms.date: 03/30/2017
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
ms.openlocfilehash: 06311e977619418c5b3fb69be518353de51e6bd5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258783"
---
# <a name="net-framework-tools"></a>.NET Framework araçları

.NET Framework araçları, .NET Framework'ü hedefleyen uygulamaları ve bileşenleri oluşturmayı, dağıtmayı ve yönetmeyi kolaylaştırmayı sağlar.

Bu bölümde açıklanan .NET Framework Araçlarının çoğu Visual Studio ile otomatik olarak yüklenir. Visual Studio 'yu indirmek için [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) sayfasını ziyaret edin.

Komut satırından tüm araçları, derleme önbelleği Görüntüleyicisi (*Shfusion.dll*) hariç olacak şekilde çalıştırabilirsiniz. Dosya Gezgini 'nden *Shfusion.dll* erişmeniz gerekir.
  
Komut satırı araçlarını çalıştırmanın en iyi yolu, Visual Studio 'nun yüklediği geliştirici kabukların birini kullanmaktır. Bu yardımcı programlar, yükleme klasörüne gitmek zorunda kalmadan araçları kolayca çalıştırmanıza olanak sağlar. Daha fazla bilgi için bkz. [Geliştirici komut satırı kabukları](/visualstudio/ide/reference/command-prompt-powershell).

> [!NOTE]
> Bazı araçlar, 32-bit bilgisayarlar veya 64-bit bilgisayarlar için özeldir. Bilgisayarınız için aracın uygun sürümünü çalıştırdığınızdan emin olun.

## <a name="in-this-section"></a>Bu bölümde

- [Al.exe (bütünleştirilmiş kod bağlayıcı)](al-exe-assembly-linker.md)  
Modüller ya da kaynak dosyalarından derleme bildirimi içeren bir dosya oluşturur.

- [Aximp.exe (Windows Forms ActiveX denetim Içeri Aktarıcı)](aximp-exe-windows-forms-activex-control-importer.md)  
Bir ActiveX denetimi için bir COM tür kitaplığındaki tür tanımlarını bir Windows Forms denetimine dönüştürür.

- [Caspol.exe (kod erişimi güvenlik Ilkesi aracı)](caspol-exe-code-access-security-policy-tool.md)  
Makine ilke düzeyi, kullanıcı ilke düzeyi ve kurumsal ilke düzeyi için güvenlik ilkesi görüntülemenize ve yapılandırmanıza olanak tanır. .NET Framework 4 ve sonrasında, bu araç, [ \<legacyCasPolicy> öğe](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) olarak ayarlanmadığı takdirde kod ERIŞIM güvenliği (CAS) ilkesini etkilemez `true` . Daha fazla bilgi için bkz. [güvenlik değişiklikleri](/previous-versions/dotnet/framework/security/security-changes).

- [Cert2spc.exe (yazılım yayımcısı sertifika test aracı)](cert2spc-exe-software-publisher-certificate-test-tool.md)  
Bir veya daha fazla X.509 sertifikasından bir Yazılım Yayımcıları Sertifikası (SPC) oluşturur. Bu araç yalnızca test içindir.

- [Certmgr.exe (Sertifika Yöneticisi aracı)](certmgr-exe-certificate-manager-tool.md)  
Sertifikaları, sertifika güven listelerini (CTL) ve sertifika çağırma listelerini (CRL) yönetir.

- [Clrver.exe (CLR sürüm aracı)](clrver-exe-clr-version-tool.md)  
Bilgisayardaki ortak dil çalışma zamanının (CLR) yüklü tüm sürümlerini raporlar.

- [CorFlags.exe (CorFlags dönüştürme aracı)](corflags-exe-corflags-conversion-tool.md)  
Taşınabilir çalıştırılabilir (PE) görüntüsünün üstbilgisine ait CorFlags bölümünü yapılandırmanıza olanak sağlar.

- [Fuslogvw.exe (bütünleştirilmiş kod bağlama günlük Görüntüleyici)](fuslogvw-exe-assembly-binding-log-viewer.md)  
Derleme hakkında, .NET Framework'ün çalışma zamanında neden derlemeyi bulamadığını tanılamanıza yardımcı olacak bilgiler görüntüler.

- [Gacutil.exe (Genel Bütünleştirilmiş Kod Önbelleği Aracı)](gacutil-exe-gac-tool.md)  
Genel derleme önbelleğinin içeriğini görüntülemenize, kullanmanıza ve önbelleği indirmenize olanak sağlar.

- [Ilasm.exe (Il Assembler)](ilasm-exe-il-assembler.md)  
Ara dil'den (IL) taşınabilir çalıştırılabilir bir (PE) dosya oluşturur. IL'in beklendiği gibi çalışıp çalışmadığını belirlemek için elde edilen çalıştırılabilir dosyayı çalıştırabilirsiniz.

- [Ildasm.exe (Il ayırıcı)](ildasm-exe-il-disassembler.md)  
Ara dil (IL) kodunu içeren taşınabilir, çalıştırılabilir (PE) dosyayı alır ve IL Derleyicisi'ne (Ilasm.exe) girdi olmaya uygun bir metin dosyası oluşturur.

- [Installutil.exe (Yükleyici Aracı)](installutil-exe-installer-tool.md)  
Belirtilen bir derlemedeki yükleyici bileşenlerini yürüterek sunucu kaynaklarını yüklemenize ve kaldırmanıza olanak verir. (Ad alanındaki sınıflarla birlikte kullanılır <xref:System.Configuration.Install> .)

- [Lc.exe (lisans derleyicisi)](lc-exe-license-compiler.md)  
Lisanslama bilgilerini içeren metin dosyalarını okur ve kaynak olarak ortak bir dil çalışma zamanı yürütülebilir dosyasına katıştırılabilen bir *. lisanslar* dosyası üretir.

- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](mage-exe-manifest-generation-and-editing-tool.md)  
Uygulama ve dağıtım bildirimleri oluşturmanıza, düzenlemenize ve imzalamanıza olanak verir. Bir komut satırı aracı olarak *Mage.exe* , hem toplu betiklerden hem de ASP.NET uygulamaları dahil diğer Windows tabanlı uygulamalardan çalıştırılabilir.

- [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, grafik Istemci)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
Komut satırı aracı Mage.exe ile aynı işlevselliği destekler, ancak Windows tabanlı bir kullanıcı arabirimi (UI) kullanır. , Komut satırı aracı *Mage.exe* aynı işlevleri destekler, ancak Windows tabanlı bir kullanıcı ARABIRIMI (UI) kullanır.

- [MDbg.exe (.NET Framework Command-Line hata ayıklayıcı)](mdbg-exe.md)  
Araç satıcılarının ve uygulama geliştiricilerin, .NET Framework ortak dil çalışma zamanını hedefleyen programlardaki hataları bulmalarına ve düzeltmelerine yardımcı olur. Bu araç, hata ayıklama hizmetleri sağlamak için çalışma zamanı hata ayıklama API kullanır.

- [Mgmtclassgen.exe (Yönetim türü kesin belirlenmiş sınıf Oluşturucu)](mgmtclassgen-exe.md)  
Belirtilen bir Windows Yönetim Araçları (WMI) sınıfı için bir erken bağlanan bir yönetilen sınıf oluşturmanıza olanak sağlar.

- [Mpgo.exe (yönetilen profil temelli Iyileştirme aracı)](mpgo-exe-managed-profile-guided-optimization-tool.md)  
Yaygın son kullanıcı senaryolarını kullanarak yerel görüntü derlemelerini ayarlamanıza olanak verir. Mpgo.exe, uygulama geliştiricisi tarafından seçilen eğitim senaryolarını kullanarak yerel görüntü uygulama derlemeleri (.NET Framework derlemeleri değil) için profil verileri oluşturmasına ve bunların kullanılmasına olanak verir.

- [Ngen.exe (yerel görüntü Oluşturucu)](ngen-exe-native-image-generator.md)  
Yerel görüntüler (işlemciye özel derlenmiş makine kodu içeren dosyalar) kullanarak yönetilen uygulamaların performansını artırır. Çalışma zamanı orijinal derlemeyi derlemek için anlık (JIT) derleyiciyi kullanmak yerine önbellekteki yerel görüntüleri kullanabilir.

- [Peverify.exe (PEVerify Aracı)](peverify-exe-peverify-tool.md)  
Microsoft ara dil (MSIL) kodunuzun ve ilişkili meta verilerinizin tür güvenlik gereksinimlerini karşılamasına yardımcı olur.

- [Regasm.exe (derleme kayıt aracı)](regasm-exe-assembly-registration-tool.md)  
Bir derleme içindeki meta veriyi okur ve gerekli girişleri kayıt defterine ekler. Bu, COM istemcilerinin .NET Framework sınıfları olarak görünmesini sağlar.

- [Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)](regsvcs-exe-net-services-installation-tool.md)  
Bir derlemeyi yükler ve kaydettirir, bir tür kitaplığı oluşturur ve belirtilen bir COM+ sürümü 1.0 uygulamasına yükler, bir sınıfa programlı şekilde eklediğiniz hizmetleri yapılandırır.

- [Resgen.exe (kaynak dosya Oluşturucu)](resgen-exe-resource-file-generator.md)  
Metin (*. txt* veya *. restext*) dosyalarını ve XML tabanlı kaynak biçimi (.*resx*) dosyalarını, bir çalışma zamanı ikili çalıştırılabilir dosyasına katıştırılabilen veya uydu derlemelerine derlenen ortak dil çalışma zamanı ikili (*. resources*) dosyalarına dönüştürür.

- [SecAnnotate.exe (.NET Security açıklaması Ekleyici Tool)](secannotate-exe-net-security-annotator-tool.md)  
`SecurityCritical` `SecuritySafeCritical` Bir derlemenin ve bölümlerini tanımlar.

- [SignTool.exe (Imza aracı)](signtool-exe.md)  
Dosyaları dijital olarak imzalar, dosyalardaki imzaları doğrular ve dosyalara zaman damgası ekler.

- [Sn.exe (tanımlayıcı ad aracı)](sn-exe-strong-name-tool.md)  
Derlemelerin tanımlayıcı adlarla oluşturulmasına yardımcı olur. Bu araç, temel yönetim, imza oluşturma ve imza doğrulaması için seçenekler sağlar.

- [SOS.dll (SOS hata ayıklama uzantısı)](sos-dll-sos-debugging-extension.md)  
İç ortak dil çalışma zamanı (CLR) ortamıyla ilgili bilgi sağlayarak, WinDbg.exe hata ayıklayıcısındaki ve Visual Studio'daki yönetilen programlarda hata ayıklamanıza yardımcı olur.

- [SqlMetal.exe (kod üretme aracı)](sqlmetal-exe-code-generation-tool.md)  
.NET Framework'ün LINQ-SQL bileşenine kod ve eşleme oluşturur.

- [Storeadm.exe (yalıtılmış depolama aracı)](storeadm-exe-isolated-storage-tool.md)  
Yalıtılmış depolamayı yönetir; kullanıcının mağazalarını listeleyen ve bunları silen seçenekler sağlar.

- [Tlbexp.exe (tür kitaplığı verme programı)](tlbexp-exe-type-library-exporter.md)  
Bir ortak dil çalışma zamanı derlemesinde tanımlanan türleri açıklayan bir tür kitaplığı oluşturur.

- [Tlbimp.exe (tür kitaplığı Içeri Aktarıcı)](tlbimp-exe-type-library-importer.md)  
Bir COM tür kitaplığında bulunan tür tanımlarını bir ortak dil çalışma zamanı derlemesindeki eşdeğer tanımlara dönüştürür.

- [Winmdexp.exe (Windows Çalışma Zamanı meta verileri dışarı aktarma aracı)](winmdexp-exe-windows-runtime-metadata-export-tool.md)  
*. Winmdobj* dosyası olarak derlenen bir .NET Framework derlemesini, hem Windows çalışma zamanı meta verileri hem de uygulama bilgilerini içeren bir *. winmd* dosyası olarak paketlenmiş Windows çalışma zamanı bir bileşene dışarı aktarır.

- [Winres.exe (Windows Forms Kaynak Düzenleyicisi)](winres-exe-windows-forms-resource-editor.md)  
Windows Forms tarafından kullanılan Kullanıcı arabirimi (UI) kaynaklarını (*. resx* veya *. resources* dosyaları) yerelleştirmenize yardımcı olur. Dizeleri çevirebilir ve ardından yerelleştirilmiş dizeleri içerecek şekilde denetimleri boyutlandırabilir, taşıyabilir ve gizleyebilirsiniz.

## <a name="related-sections"></a>İlgili bölümler

- [WPF araçları](/previous-versions/ms742404(v=vs.110))  
İsXPS uyumluluk aracı (isXPS.exe) ve performans profil oluşturma araçları gibi araçları içerir.

- [Windows Communication Foundation Araçları](../wcf/tools.md)  
Windows Communication Foundation (WCF) uygulamalarını oluşturmanızı, dağıtmanızı ve yönetmenizi kolaylaştıran araçlar içerir.
