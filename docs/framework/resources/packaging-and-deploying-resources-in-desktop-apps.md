---
title: "Masaüstü Uygulamalarında Paketleme ve Dağıtma Kaynakları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- single resource assembly
- satellite assemblies
- default culture for applications
- names [.NET Framework], resources
- fallback process for resources
- grouping cultures
- application resources, deploying
- application resources, naming conventions
- culture, packaging and deploying resources
- resource files, naming conventions
- packaging application resources
- application resources, fallback processes
- resource files, fallback processes
- localizing resources
- neutral cultures
ms.assetid: b224d7c0-35f8-4e82-a705-dd76795e8d16
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f170c3e7174b231153a9e201f617faa786291056
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="packaging-and-deploying-resources-in-desktop-apps"></a>Masaüstü Uygulamalarında Paketleme ve Dağıtma Kaynakları
Uygulamaları kullanan üzerinde .NET Framework kaynak tarafından temsil edilen Yöneticisi, <xref:System.Resources.ResourceManager> yerelleştirilmiş kaynaklar almak için sınıf. Kaynak Yöneticisi'ni bir hub ve bağlı bileşen modeli paketini ve kaynakları dağıtmak için kullanıldığını varsayar. Hub nonlocalizable yürütülebilir kod ve bağımsız olarak adlandırılan tek bir kültür için kaynakları içeren ana derlemedir veya varsayılan kültür. Geri dönüş kültürü uygulama için varsayılan kültürdür; Bu kültürdür yerelleştirilmiş kaynaklar bulunamazsa, kaynakları kullanılır. Her bağlı bileşen tek bir kültür için kaynakları içerir, ancak herhangi bir kod içermiyor bir uydu derleme bağlanır.  
  
 Bu model için çeşitli avantajları vardır:  
  
-   Bir uygulamayı dağıttıktan sonra yeni kültürler için kaynaklar artımlı olarak ekleyebilirsiniz. Kültüre özgü kaynakları sonraki geliştirilmesini önemli miktarda zaman gerektirdiğinden bu, ana uygulamanızı ilk bırakın ve daha sonraki bir tarihte kültüre özgü kaynakları teslim etmek sağlar.  
  
-   Güncelleştirme ve uygulama derlemeden uygulamanın uydu derlemelerini değiştirin.  
  
-   Belirli bir kültür için gereken kaynakları içeren uydu derlemelerini yüklemek bir uygulama gerekiyor. Bu, sistem kaynaklarının kullanımını önemli ölçüde azaltabilir.  
  
 Ancak, ayrıca vardır dezavantajları Bu model için:  
  
-   Kaynaklar birden çok kümesini yönetmeniz gerekir.  
  
-   Test çeşitli yapılandırmaları gerekir çünkü bir uygulamayı test etmek ilk maliyetini artırır. Uzun vadede bunu daha kolay ve test ve birkaç paralel uluslararası sürümleri korumak için daha birçok uydunuz ile bir çekirdek uygulamayı test etmek daha ucuz olacağını unutmayın.  
  
## <a name="resource-naming-conventions"></a>Kaynak Adlandırma Kuralları  
 Uygulamanızın kaynak paketini oluşturduğunuzda ortak dil çalışma zamanı bekliyor kaynak adlandırma kurallarını kullanarak bunları adı olmalıdır. Çalışma zamanı kaynak kültür adıyla tanımlar. Her kültür genellikle bir dil ile ilişkili bir iki harf, küçük harf kültür adı birleşimidir benzersiz bir ad verilir ve gerekirse, iki harf, büyük alt adı ilişkili bir ülke veya bölge. Alt adı bir tire (-) ayrılmış kültür adı izler. Ja-JP Japonya'da en-US Amerika Birleşik Devletleri'nde, de-DE Avusturya konuşulan gibi Almanca için Almanya veya de AT konuşulan gibi Almanca için konuşulan olarak İngilizce konuşulan gibi Japonca için örnekler. Bkz: [Ulusal dil desteği (NLS) API Başvurusu](http://go.microsoft.com/fwlink/?LinkId=200048) Git genel Developer Center'da kültür adları tam bir listesi.  
  
> [!NOTE]
>  Kaynak dosyaları oluşturma hakkında daha fazla bilgi için bkz: [oluşturma kaynak dosyaları](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md) ve [uydu derlemeleri oluşturma](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).  
  
<a name="cpconpackagingdeployingresourcesanchor1"></a>   
## <a name="the-resource-fallback-process"></a>Kaynak Geri Dönüş İşlemi  
 Paketleme ve dağıtma kaynakları için hub ve bağlı bileşen modeli uygun kaynakları bulmak için bir geri dönüş işlemi kullanır. Bir uygulama kullanılamıyor yerelleştirilmiş bir kaynak isterse, kullanıcının uygulamayla en yakından eşleşen uygun bir geri dönüş kaynak kullanıcının istemek ve bir özel durum oluşturur ortak dil çalışma zamanı kültürler hiyerarşisini arar olarak yalnızca bir Son çare. Uygun bir kaynak bulunursa, hiyerarşinin her düzeyinde çalışma zamanı kullanır. Kaynak bulunmazsa, İleri düzeyde aramaya devam eder.  
  
 Arama performansını artırmak için uygulamanız <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliği ana derlemenizi ve ana derlemenizi ile çalışacak dilden adını geçirin.  
  
> [!TIP]
>  Kullanmak mümkün olabilir [ \<relativeBindForResources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) kaynak geri dönüş işlemi ve çalışma zamanı yoklamaları için kaynak derlemeleri işlemi iyileştirmek için yapılandırma öğesi. Daha fazla bilgi için bkz: [kaynak geri dönüş işlemi en iyi duruma getirme](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#Optimizing) bölümü.  
  
 Geri dönüş işlemi kaynak aşağıdaki adımları içerir:  
  
1.  Çalışma zamanı ilk denetimleri [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md) istenen kültürü uygulamanız için eşleşen bir derlemenin.  
  
     Birçok uygulama tarafından paylaşılan kaynak derlemeleri genel derleme önbelleği depolayabilirsiniz. Bu kaynakların belirli kümeleri oluşturduğunuz her uygulamada dizin yapısını eklemek zorunda kalmaktan kurtarır. Çalışma zamanı derlemesine başvuru bulursa, istenen kaynak assembly arar. Derlemede giriş bulursa, istenen kaynak kullanır. Giriş bulamazsa arama devam eder.  
  
2.  Çalışma zamanı sonraki şu anda yürütülen bütünleştirilmiş istenen kültürü eşleşen bir dizin için dizin denetler. Bu dizin bulunursa, geçerli uydu derlemesi istenen kültürü için bu dizine arar. Çalışma zamanı, ardından istenen kaynak için uydu derlemesi arar. Derlemede kaynak bulursa, onu kullanır. Kaynak bulamazsa arama devam eder.  
  
3.  Çalışma zamanı sonraki uydu derlemesi isteğe bağlı olarak yüklü olup olmadığını belirlemek için Windows Installer sorgular. Bu nedenle, yükleme işlemini yürütür, derleme yükler ve onu veya istenen kaynak arar. Derlemede kaynak bulursa, onu kullanır. Kaynak bulamazsa arama devam eder.  
  
4.  Çalışma zamanı başlatır <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> uydu derlemesi bulamıyor belirtmek için olay. Olayını işlemek seçerseniz, olay işleyicisi olan kaynakları arama için kullanılacak uydu derlemesine başvuru döndürebilir. Aksi takdirde, olay işleyicisini döndürür `null` ve aramaya devam eder.  
  
5.  Çalışma zamanı sonraki aramaları genel derleme önbelleği yeniden, bu süre istenen üst derlemenin kültür. Ana derleme genel derleme önbelleğinde varsa, çalışma zamanı derlemesi istenen kaynak için arar.  
  
     Üst kültür uygun geri dönüş kültür olarak tanımlanır. Geri dönüş aday olarak üst herhangi bir özel durum atma için tercih edilen kaynaktır sağlamak için göz önünde bulundurun. Bu işlem kaynakları yeniden sağlar. Yalnızca alt kültür istenen kaynak yerelleştirme gerekmez, üst düzeyde belirli bir kaynak içermelidir. Örneğin, tr (nötr İngilizce) için uydu derlemelerini sağlarsanız tr-GB (İngilizce konuşulan İngiltere'gibi) ve en-US (İngilizce), Amerika Birleşik Devletleri'nde konuşulan gibi tr uydu ortak terminoloji, tr-GB ve en-US uydunuz içerecektir farklı koşullar için geçersiz kılmaları sağlayabilir.  
  
6.  Çalışma zamanı sonraki directory şu anda yürütülen derlemenin üst dizini içerip içermediğini denetler. Üst dizini zaten varsa, çalışma dizini geçerli uydu derleme üst kültür için arar. Derleme bulursa, çalışma zamanı derlemesi istenen kaynak için arar. Kaynak bulursa, onu kullanır. Kaynak bulamazsa arama devam eder.  
  
7.  Çalışma zamanı üst uydu derlemesi isteğe bağlı olarak yüklü olup olmadığını belirlemek için Windows Installer sonraki sorgular. Bu nedenle, yükleme işlemini yürütür, derleme yükler ve onu veya istenen kaynak arar. Derlemede kaynak bulursa, onu kullanır. Kaynak bulamazsa arama devam eder.  
  
8.  Çalışma zamanı başlatır <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> uygun bir geri dönüş kaynak bulamıyor belirtmek için olay. Olayını işlemek seçerseniz, olay işleyicisi olan kaynakları arama için kullanılacak uydu derlemesine başvuru döndürebilir. Aksi takdirde, olay işleyicisini döndürür `null` ve aramaya devam eder.  
  
9. Çalışma zamanı sonraki aramaları olduğu gibi birçok olası düzeyleri aracılığıyla önceki üç adımı derlemeleri üst. Her kültür tarafından tanımlanan yalnızca bir üst öğeye sahip <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> özelliği, ancak üst öğesi kendi üst olabilir. Üst Ara kültürler durakları bir kültür zaman 's <xref:System.Globalization.CultureInfo.Parent%2A> özelliği döndürür <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>sabit kültür üst kültür veya kaynaklara sahip olabilecek bir kültür değil kabul geri dönüş, kaynak için;.  
  
10. Başlangıçta belirtilen kültür ve tüm üst aranır ve kaynak yine bulunamazsa, kaynak varsayılan (Temel) kültürü için kullanılır. Genellikle, varsayılan kültür için kaynaklar ana uygulama bütünleştirilmiş kodunda dahil edilir. Ancak, bir değer belirleyebilirsiniz <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> için <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> özelliği <xref:System.Resources.NeutralResourcesLanguageAttribute> kaynaklar için son geri dönüş konumu ana derleme yerine bir uydu derleme olduğunu belirtmek için öznitelik.  
  
    > [!NOTE]
    >  Varsayılan kaynak ana bütünleştirilmiş kod ile derlenebilir yalnızca kaynak değil. Kullanarak bir uydu derleme belirtmediğiniz sürece <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliği, ultimate geri dönüş (son üst öğe) değil. Bu nedenle, varsayılan bir kaynak kümesi her zaman ana derlemenizi eklemeniz önerilir. Bu, oluşturulan gelen özel durumları önlemeye yardımcı olur. Culturally belirli olmasa bile, varsayılan ekleyerek tüm kaynaklar için bir geri dönüş sağlayın ve bu en az bir kaynak olun kaynak dosyası her zaman kullanıcı için mevcuttur.  
  
11. Son olarak, çalışma zamanı (Temel) varsayılan kültürü için bir kaynak bulamazsa bir <xref:System.Resources.MissingManifestResourceException> veya <xref:System.Resources.MissingSatelliteAssemblyException> kaynak bulunamadı belirtmek için özel durum.  
  
 Örneğin, uygulama isteklerini İspanyolca (Meksika) (es-MX kültür) için yerelleştirilmiş bir kaynak varsayalım. Çalışma zamanı, Genel Derleme Önbelleği ilk es eşleşen derleme için arama yapar.-MX, bulma değil ancak. Çalışma zamanı sonra es MX dizini için şu anda yürütülen bütünleştirilmiş dizinini arar. Başarısız olan, çalışma zamanı genel derleme önbelleği yeniden için uygun geri dönüş kültürü yansıtan bir üst derleme aramaların — bu durumda, es (İspanyolca). Ana derleme bulunmazsa, karşılık gelen kaynak bulana kadar çalışma zamanı üst derlemeler es MX kültür için tüm olası düzeylerini arar. Bir kaynak bulunamazsa, çalışma zamanı için varsayılan kültürü kaynak kullanır.  
  
<a name="Optimizing"></a>   
### <a name="optimizing-the-resource-fallback-process"></a>Kaynak Geri Dönüş İşlemini En İyi Duruma Getirme  
 Aşağıdaki koşullar altında çalışma zamanı uydu derlemelerini kaynaklarında arar işlem iyileştirebilirsiniz  
  
-   Uydu derlemeleri kod derleme ile aynı konumda dağıtılır. Kod derleme yüklüyse [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md), uydu derlemeleri genel derleme önbelleğinde de yüklenir. Kod derleme bir dizinde yüklüyse, uydu derlemelerini bu dizinin kültüre özgü klasörlere yüklenir.  
  
-   Uydu derlemeleri isteğe bağlı olarak yüklü değildir.  
  
-   Uygulama kodu işlemiyor <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.  
  
 Araştırması için uydu derlemelerini dahil ederek en iyi duruma [ \<relativeBindForResources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) öğesi ve ayarı kendi `enabled` özniteliğini `true` gösterildiği gibi uygulama yapılandırma dosyası Aşağıdaki örnekte.  
  
```xml  
<configuration>  
   <runtime>  
      <relativeBindForResources enabled="true" />  
   </runtime>  
</configuration>  
```  
  
 Uydu derlemeleri için en iyi duruma getirilmiş araştırma, bir katılımı özelliğidir. Diğer bir deyişle, çalışma zamanı konusunda belgelenen adımları izler [kaynak geri dönüş işlem](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) sürece [ \<relativeBindForResources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) öğesidir uygulamanın içinde mevcut yapılandırma dosyası ve onun `enabled` özniteliği `true`. Bu durumda, uydu derlemesi için yoklama işlemi şu şekilde değiştirilir:  
  
-   Çalışma zamanı üst kod derleme konumunu uydu derlemesi için araştırma için kullanır. Ana derleme genel derleme önbelleğinde yüklüyse, çalışma zamanı önbelleğinde ancak uygulama dizinindeki araştırmaları. Ana derleme bir uygulama dizininde yüklüyse, çalışma zamanı uygulama dizinindeki ancak genel derleme önbelleğinde araştırmaları.  
  
-   Çalışma zamanı uydu derlemelerinin isteğe bağlı yükleme için Windows Installer sorgu değil.  
  
-   Belirli kaynak assembly için yoklama başarısız olursa, çalışma zamanı değil Yükselt <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.  
  
### <a name="ultimate-fallback-to-satellite-assembly"></a>Uydu Derlemesi için Ultimate Geri Dönüş  
 İsteğe bağlı olarak, ana bütünleştirilmiş koddan kaynakları kaldırın ve çalışma zamanı ultimate geri dönüş kaynakları için belirli bir kültür karşılık gelen bir uydu derlemesinden yükleyeceğini belirtin. Geri dönüş işlemi denetlemek için kullandığınız <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=nameWithType> oluşturucusu ve için bir değer sağlamanız <xref:System.Resources.UltimateResourceFallbackLocation> ana derleme ya da bir uydu derleme Kaynak Yöneticisi'ni geri dönüş kaynakları ayıklamak olup olmadığını belirten parametre.  
  
 Aşağıdaki örnek kullanır <xref:System.Resources.NeutralResourcesLanguageAttribute> Fransızca (fr) dil için bir uydu derleme uygulamanın geri dönüş kaynakları depolamak için öznitelik.  Örnek bir tek bir dize kaynağı tanımlayan iki metin tabanlı kaynak dosyaların sahip `Greeting`. İlk olarak, resources.fr.txt, Fransızca Dil kaynak içeriyor.  
  
```  
Greeting=Bon jour!  
```  
  
 İkincisi, resources,ru.txt, Rusça Dil kaynak içeriyor.  
  
```  
Greeting=Добрый день  
```  
  
 Bu iki dosyayı .resources dosyaları çalıştırarak derlenen [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) komut satırından.  Fransızca Dil kaynağı için bir komut şöyledir:  
  
 **Resgen.exe resources.fr.txt**  
  
 Rusça Dil kaynağı için bir komut şöyledir:  
  
 **Resgen.exe resources.ru.txt**  
  
 .Resources dosyaları çalıştırarak dinamik bağlantı kitaplıkları katıştırılan [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) komuttan satır Fransızca Dil kaynağı için şu şekilde:  
  
 **Al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**  
  
 ve aşağıdaki gibi Rusça Dil kaynak için:  
  
 **Al /t:lib /embed:resources.ru.resources /culture:ru /out:ru\Example1.resources.dll**  
  
 Uygulama kaynak koduna Example1.cs veya Example1.vb adındaki bir dosyada yer alıyor. İçerdiği <xref:System.Resources.NeutralResourcesLanguageAttribute> varsayılan uygulama kaynağı fr alt dizinindeki olduğunu belirtmek için öznitelik. Kaynak Yöneticisi'ni başlatır, değerini alır `Greeting` kaynak ve konsola görüntüler.  
  
 [!code-csharp[Conceptual.Resources.Packaging#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
 [!code-vb[Conceptual.Resources.Packaging#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]  
  
 C# kaynak kodu komut satırından aşağıdaki gibi sonra hazırlayabilirsiniz:  
  
 **CSC Example1.cs**  
  
 Visual Basic derleyici komut çok benzer:  
  
 **Vbc Example1.vb**  
  
 Ana derlemede katıştırılmış kaynak olduğundan, kullanarak derleme gerekmez `/resource` geçin.  
  
 Örnek dilinden Rusça dışındaki herhangi bir sistemde çalıştırdığınızda, aşağıdaki çıkış görüntüler:  
  
```  
Bon jour!  
```  
  
## <a name="suggested-packaging-alternative"></a>Önerilen Paketleme Alternatifi  
 Zaman veya bütçe kısıtlamaları kaynaklar için uygulamanızın destekleyen her bir alt kümesi oluşturma engelleyebilir. Bunun yerine, tüm subcultures ilgili bir üst kültür kullanabilir, tek bir uydu derlemesi oluşturabilirsiniz. Örneğin, bölgeye özgü İngilizce kaynakları isteği kullanıcılar tarafından alınan tek bir İngilizce uydu derlemesi (TR) ve bölgeye özgü Almanca kaynakları isteyen kullanıcılar için tek Almanca uydu derlemesi (de) sağlayabilir. Örneğin, Almanca olarak Almanya (de-DE), konuşulan gibi Avusturya (AT de) ve İsviçre (CH de) Almanca uydu derlemesi (de) geri döner ister. Varsayılan kaynaklar son geri dönüş ve bu nedenle, uygulamanızın kullanıcılarıyla çoğunluğu tarafından istenen kaynakları böylece bu kaynakları dikkatle seçin. Bu yaklaşım, daha az culturally özeldir, ancak uygulamanızın yerelleştirme maliyetlerini önemli ölçüde azaltabilir kaynakları dağıtır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)  
 [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)  
 [Kaynak Dosyaları Oluşturma](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Uydu Derlemeleri Oluşturma](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
