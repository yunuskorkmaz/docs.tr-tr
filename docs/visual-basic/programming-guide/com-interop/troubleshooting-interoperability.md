---
title: "Birlikte Çalışabilirlik İle İlgili Sorun Giderme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability [Visual Basic]
- interoperability, troubleshooting
- COM interop [Visual Basic], troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 988d07fe08a6a78ae295d13f694c55a3b8f9d2e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-interoperability-visual-basic"></a>Birlikte Çalışabilirlik İle İlgili Sorun Giderme (Visual Basic)
Ne zaman, çalışmanız COM ile yönetilen kod arasında [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], bir veya daha fazla aşağıdaki ortak sorunları karşılaşabilirsiniz.  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a>Birlikte çalışma hazırlama  
 Bazen olmayan veri türlerini kullanmak zorunda kalabilirsiniz parçası [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Birlikte çalışma derlemeleri COM nesneleri için iş çoğunu işleyecek ancak yönetilen nesneleri com'a kullanılan veri türünü kontrol gerekebilir Örneğin, sınıf kitaplıkları yapılarda belirtmelisiniz `BStr` yönetilmeyen Visual Basic 6.0 ve önceki sürümleri tarafından oluşturulan COM nesnelerini gönderilen dizelerde türü. Böyle durumlarda, kullandığınız <xref:System.Runtime.InteropServices.MarshalAsAttribute> yönetilmeyen türleri olarak açığa çıkarılması yönetilen türler neden özniteliği.  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a>Yönetilmeyen kod için dışarı aktarma sabit uzunluklu dizeler  
 Visual Basic 6.0 ve önceki sürümlerinde, bir null sonlandırma karakteri olmadan bayt dizisi olarak dizeleri COM nesnelerine dışarı aktarılır. Diğer dilleri ile uyumluluk için Visual Basic .NET dizeleri dışarı aktarılırken bir sonlandırma karakter içerir. Sonlandırma karakter dizileri eksikliği dizeleri dışarı aktarmak için bu uyumsuzluk adres etmenin en iyi yolu olan `Byte` veya `Char`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a>Devralma hiyerarşileri dışarı aktarma  
 Yönetilen sınıf hiyerarşileri COM nesneleri olarak kullanıma sunulan zaman düzleştirmek çıkışı. Bir taban sınıf sahip bir üye tanımlayın ve taban sınıf içinde bir COM nesnesi olarak sunulan türetilmiş sınıf devralma, örneğin, türetilmiş sınıf COM nesnesinde kullanan istemciler devralınan üyeleri kullanmanız mümkün olmaz. Taban sınıfı üyeleri erişilebilir COM nesneleri yalnızca bir temel sınıf örnekleri ve ardından yalnızca temel sınıfı bir COM nesnesi olarak da oluşturulur.  
  
## <a name="overloaded-methods"></a>Aşırı yüklenmiş yöntemler  
 Oluşturabileceğiniz rağmen yöntemleriyle aşırı [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], COM tarafından desteklenmez Aşırı yüklenmiş yöntemler içeren bir sınıf bir COM nesnesi olarak sunulduğunda, yeni yöntemi adları aşırı yüklenmiş yöntemler için oluşturulur.  
  
 Örneğin, iki aşırı olan bir sınıfı göz önünde bulundurun `Synch` yöntemi. Sınıfı COM nesnesi olarak sunulduğunda, yeni oluşturulan yöntemi adları olabilir `Synch` ve `Synch_2`.  
  
 Yeniden adlandırma COM nesnesi Tüketiciler için iki sorunlara neden olabilir.  
  
1.  İstemcileri oluşturulan yöntem adları beklememeniz.  
  
2.  Yeni aşırı sınıf veya onun temel sınıfı eklendiğinde COM nesnesi olarak sunulan sınıfında oluşturulan yöntemi adlarını değiştirebilirsiniz. Bu sürüm oluşturma sorunlarına yol açabilir.  
  
 Her iki sorunları çözmek için her yöntemi aşırı COM nesneleri olarak gösterilen nesneleri geliştirirken kullanmak yerine benzersiz bir ad verin.  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a>COM birlikte çalışma derlemeleri nesnelerde kullanımı  
 Yönetilen kod değişikliklerini temsil ettikleri COM nesneleri için neredeyse olmaları durumunda olarak birlikte çalışma derlemeleri kullanın. Ancak, sarmalayıcılar ve gerçek COM nesneleri olduklarından, birlikte çalışma derlemeleri ve standart derlemeleri kullanma arasındaki bazı farklar vardır. Bu alanlar farkının Etkilenme sınıf ve veri türleri için parametreler ve dönüş değerleri şunlardır.  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a>Her iki arabirimde sunulan sınıfları ve sınıfları  
 Standart derlemelerde sınıfları, bir arabirim ve COM sınıfı temsil eden bir sınıf olarak birlikte çalışma derlemeleri COM sınıfları sunulur. Arabirim adı, COM sınıfı için aynıdır. Birlikte çalışma sınıfın adını, özgün COM sınıfı ile aynıdır, ancak "Sınıf" sözcüğüyle eklenir. Örneğin, bir COM nesnesi için bir birlikte çalışma derlemesine başvuru içeren bir proje olduğunu varsayalım. COM sınıfı adlandırılmışsa `MyComClass`, IntelliSense ve Nesne Tarayıcısı adlı bir arabirim göster `MyComClass` ve adlı bir sınıf `MyComClassClass`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a>Bir .NET Framework sınıf örneklerini oluşturma  
 Genellikle, örneğini oluşturduğunuz bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kullanarak sınıfı `New` bir sınıf adı deyimiyle. Birlikte çalışma derlemesi tarafından temsil edilen bir COM sınıfı sahip olduğu kullanım bir örneği `New` deyimi bir arabirime sahip. COM sınıfı kullanmadığınız sürece bir `Inherits` deyimi, bir sınıf olarak arabirimi kullanabilirsiniz. Aşağıdaki kodu nasıl oluşturulduğunu gösteren bir `Command` Microsoft ActiveX veri nesneleri 2.8 kitaplığı COM nesneye bir başvurusu olan bir proje nesnesinde:  
  
 [!code-vb[VbVbalrInterop#20](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 Ancak, türetilmiş bir sınıf için temel olarak COM sınıfı kullanıyorsanız, aşağıdaki kod olduğu gibi COM sınıfı temsil eden birlikte çalışma sınıf kullanmanız gerekir:  
  
 [!code-vb[VbVbalrInterop#21](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  Birlikte çalışma derlemeleri COM sınıfları temsil eden arabirimler örtük olarak uygular. Kullanmayı denemek `Implements` bu arabirimleri veya bir hata uygulamak için deyimi neden olur.  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a>Veri türleri için parametreler ve dönüş değerleri  
 Standart derlemeleri üyeleri, özgün nesne bildiriminde kullanılanlardan farklı veri türleri birlikte çalışma derlemesi üyeleri olabilir. Birlikte çalışma derlemeleri COM türlerini uyumlu ortak dil çalışma zamanı türü örtük olarak Dönüştür. ancak, her iki çalışma zamanı hataları önlemek için kullanılan veri türlerine dikkat etmeniz gerekir. Örneğin, Visual Basic 6.0 ve önceki sürümlerinde, türü değerleri oluşturulan COM nesnelerini içinde `Integer` varsayın [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] eşdeğer türü `Short`. Kullanmadan önce içeri aktarılan üyeleri özelliklerini incelemek için Nesne Tarayıcısı kullanmanız önerilir.  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a>Modül düzeyi COM yöntemleri  
 Çoğu COM nesneleri, COM sınıfı kullanarak bir örneğini oluşturarak kullanılır `New` anahtar sözcüğünü ve ardından nesnesinin yöntemleri çağırma. Bu kural için bir özel içerir içeren COM nesneleri `AppObj` veya `GlobalMultiUse` COM sınıfları. Bu tür sınıflar modül düzeyi Visual Basic .NET sınıfları yöntemlerinde benzer. Örtük olarak Visual Basic 6.0 ve önceki sürümleri gibi nesnelerin örneklerini sizin için kendi yöntemlerini birini çağırın ilk kez oluşturun. Örneğin, Visual Basic 6. 0 ' Microsoft DAO 3.6 Nesne Kitaplığı ve çağrı başvuru ekleyebileceğiniz `DBEngine` örneği ilk oluşturmadan yöntemi:  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET kendi yöntemlerini kullanabilmeniz için önce her zaman COM nesnelerinin örneklerini oluşturmanız gerekir. Visual Basic'te bu yöntemleri kullanmak için istenen sınıfı bir değişken bildirme ve nesne nesne değişkenine atamak için yeni anahtar sözcük kullanma. `Shared` Anahtar sözcüğü kullanılabilir olduğundan emin olmak istediğinizde bu yalnızca bir sınıf örneği oluşturulur.  
  
 [!code-vb[VbVbalrInterop#23](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a>Olay işleyicileri işlenmemiş hataları  
 Bir ortak birlikte çalışma sorun COM nesneleri tarafından başlatılan olayları işlemek olay işleyicileri hataları içerir. Bu tür hatalar özellikle kullanarak hatalara karşı denetleyin yoksayılır `On Error` veya `Try...Catch...Finally` deyimleri. Örneğin, aşağıdaki örnek, Microsoft ActiveX veri nesneleri 2.8 kitaplığı COM nesneye bir başvurusu olan bir Visual Basic .NET projesinden olur.  
  
 [!code-vb[VbVbalrInterop#24](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 Bu örnek, beklendiği gibi bir hata oluşturur. Ancak, aynı örneği olmadan çalışırsanız `Try...Catch...Finally` bloğu, hatayı göz ardı edilir gibi kullandıysanız `OnError Resume Next` deyimi. Hata işleme olmadan sessizce sıfıra bölme başarısız olur. İşlenmeyen özel durum hataları gibi hataları hiçbir zaman yükseltmek için özel durum olayları COM nesneleri işlemek olay işleyicileri işleme çeşit kullanmak önemlidir.  
  
### <a name="understanding-com-interop-errors"></a>COM birlikte çalışma hataları anlama  
 Hata işleme olmadan birlikte çalışma çağrıları genellikle çok az bilgisi sağlayın hatalar oluşturur. Mümkün olduğunda, yapılandırılmış hata ortaya çıkan sorunları hakkında daha fazla bilgi sağlamak için işleme kullanın. Uygulamaları ayıklarken bu özellikle yararlı olabilir. Örneğin:  
  
 [!code-vb[VbVbalrInterop#25](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 Özel durum nesnesi içeriğini inceleyerek hata açıklaması, HRESULT ve COM hatalarının kaynağını gibi bilgiler bulabilirsiniz.  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a>ActiveX denetimi sorunları  
 Visual Basic 6.0 ile iş çoğu ActiveX denetimlerini sorun Visual Basic .NET ile birlikte çalışır. Ana kapsayıcı denetimleri veya görsel olarak diğer denetimleri içeren denetimler durumlardır. Bazı örnekler ile düzgün çalışmıyor eski denetimlerin [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] aşağıdaki gibidir:  
  
-   Microsoft Forms 2.0 çerçeve denetimi  
  
-   Yukarı-Aşağı denetimi döndürme denetimi olarak da bilinir  
  
-   Sheridan sekme denetimi  
  
 Desteklenmeyen ActiveX denetimi sorunları için yalnızca birkaç geçici çözümler vardır. Mevcut denetimleri geçirebilirsiniz [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] özgün kaynak kodunun sahipseniz. Aksi durumda, güncelleştirilmiş yazılım satıcıları ile denetleyebilirsiniz. NET uyumlu sürümlerini değiştirmek için denetimleri ActiveX denetimlerini desteklenmiyor.  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a>Denetimleri ByRef geçirme ReadOnly özellikleri  
 Visual Basic .NET, geçirdiğinizde COM hataları gibi "Hata 0x800A017F CTL_E_SETNOTSUPPORTED" bazen başlatır `ReadOnly` bazı eski ActiveX denetimleri olarak özelliklerini `ByRef` diğer yordamlar için parametreler. Visual Basic 6.0 benzer yordam çağrıları hata yükseltmeyin ve değerine göre geçirilen gibi parametreleri kabul edilir. Bir özellik olmayan bir özellik değiştirmeye çalıştığınız Visual Basic .NET hata iletisi gösterir `Set` yordamı.  
  
 Çağrılan yordamı erişiminiz varsa, kullanarak bu hatayı önleyebilirsiniz `ByVal` kabul parametreleri bildirmek için anahtar sözcüğü `ReadOnly` özellikleri. Örneğin:  
  
 [!code-vb[VbVbalrInterop#26](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 Çağrılan yordamı için kaynak koduna erişim yoksa özelliğini parantezler GetTypeId yordamını içinde ek bir dizi ekleyerek değere göre geçirilecek şekilde zorlayabilirsiniz. Örneğin, Microsoft ActiveX veri nesneleri 2.8 kitaplığı COM nesneye bir başvurusu olan bir proje ile kullanabilirsiniz:  
  
 [!code-vb[VbVbalrInterop#27](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a>Birlikte çalışma kullanıma derlemeleri dağıtma  
 COM arabirimleri kullanıma derlemeleri dağıtma benzersiz zorluklara gösterir. Örneğin, ayrı uygulamalar aynı COM bütünleştirilmiş koda başvurduğunuzda olası bir sorun oluşur. Bu durum, bir derlemeyi yeni bir sürümü yüklü olduğundan ve başka bir uygulama derleme eski sürümünü kullanmaya devam yaygındır. DLL paylaşan derleme kaldırırsanız, kasıtsız olarak bunu kullanılamaz için diğer derlemelerden duruma getirebilirsiniz.  
  
 Bu sorunu önlemek için paylaşılan derlemeleri genel derleme önbelleği (GAC) yükleyin ve bir MergeModule bileşeni için kullanmanız gerekir. GAC içinde uygulama yükleyemiyorsanız sürüme özgü alt dizinindeki Commonfılesfolder için yüklenmelidir.  
  
 Paylaşılmayan derlemeler, çağıran uygulama ile dizinde yan yana bulunmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [COM birlikte çalışma](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [İzlenecek yol: COM nesnelerinde kalıtım uygulama](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Genel Derleme Önbelleği](../../../framework/app-domains/gac.md)
