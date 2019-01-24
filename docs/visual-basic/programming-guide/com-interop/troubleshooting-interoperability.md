---
title: Birlikte Çalışabilirlik İle İlgili Sorun Giderme (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 413c9331611d3406c13df58f25db1ef0255339b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517675"
---
# <a name="troubleshooting-interoperability-visual-basic"></a>Birlikte Çalışabilirlik İle İlgili Sorun Giderme (Visual Basic)
Ne zaman, birlikte çalışmak COM ve yönetilen kodu arasında [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], bir veya daha fazla aşağıdaki yaygın sorunların karşılaşabilirsiniz.  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a> Birlikte çalışma hazırlama  
 Bazen, olmayan veri türlerini kullanmak zorunda kalabilirsiniz parçası [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Birlikte çalışma bütünleştirilmiş kodları COM nesneleri için işin çoğunu işlemek, ancak yönetilen nesneleri com'a kullanılan veri türlerini denetlemek olabilir Örneğin, sınıf kitaplıkları yapılarda belirtmelisiniz `BStr` yönetilmeyen Visual Basic 6.0 ve önceki sürümleri ile oluşturulan COM nesnelerini gönderilen dizelerde türü. Bu gibi durumlarda, kullandığınız <xref:System.Runtime.InteropServices.MarshalAsAttribute> neden yönetilmeyen tür açığa yönetilen türler için öznitelik.  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a> Sabit uzunluklu dizeler yönetilmeyen koda dışarı aktarma  
 Visual Basic 6.0 ve önceki sürümlerinde, sonlandırma boş karakteri olmadan bayt dizisi olarak dizeleri için COM nesneleri dışarı aktarılır. Diğer dilleri ile uyumluluk için Visual Basic .NET dizeleri dışarı aktarılırken bir sonlandırma karakter içerir. Bu uyumsuzluk yönelik en iyi yolu bir sonlandırma karakter dizileri eksik dizeleri dışa aktarılmamasıdır `Byte` veya `Char`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a> Devralma hiyerarşilerini dışarı aktarma  
 Sınıf Hiyerarşiler COM nesneleri olarak kullanıma sunulan zaman düzleştirmek kullanıma yönetilen. Örneğin, bir temel sınıf üyesi ile tanımlayın ve ardından bir COM nesnesi olarak sunulan bir türetilmiş sınıf içinde temel sınıf devralma, türetilmiş sınıf içinde COM nesnesi kullanan istemciler devralınan üyeleri kullanmak mümkün olmayacaktır. Temel sınıf üyelerinin erişilebilir COM nesneleri yalnızca bir temel sınıfın bir örneği ve yalnızca temel sınıfı bir COM nesnesi olarak da oluşturulur.  
  
## <a name="overloaded-methods"></a>Aşırı yüklenmiş yöntemler  
 Visual Basic ile aşırı yüklenmiş yöntemler oluşturabilirsiniz, ancak bunlar COM tarafından desteklenmiyor Aşırı yüklenmiş yöntemler içeren bir sınıfı bir COM nesnesi olarak sunulduğunda, yeni yöntem adları için aşırı yüklenmiş yöntemler oluşturulur.  
  
 Örneğin, iki aşırı yüklemesi olan bir sınıf düşünün `Synch` yöntemi. Sınıfı bir COM nesnesi olarak sunulduğunda, yeni oluşturulan yöntem adları olabilir `Synch` ve `Synch_2`.  
  
 Yeniden adlandırma, COM nesnesinin Tüketiciler için iki sorunlara neden olabilir.  
  
1.  İstemciler, oluşturulan yöntem adları edemeyeceğiniz.  
  
2.  Yeni aşırı sınıf ya da onun temel sınıfından eklendiğinde bir COM nesnesi olarak kullanıma sunulan sınıfında oluşturulan yöntem adlarını değiştirebilirsiniz. Bu sürüm sorunlara neden olabilir.  
  
 Her iki sorunları çözmek için her bir yöntemin COM nesneleri olarak kullanıma sunulacak nesneleri geliştirirken, aşırı yükleme yerine benzersiz bir ad verin.  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a> Birlikte çalışma derlemeleriyle COM nesnelerinin kullanın  
 Yönetilen kod değişikliklerini temsil ettikleri COM nesneleri için neredeyse olmaları durumunda gibi birlikte çalışma bütünleştirilmiş kodları kullanın. Ancak, bunlar sarmalayıcılar ve gerçek COM nesneleri olduğundan, birlikte çalışma bütünleştirilmiş kodları ve standart derlemeler arasındaki bazı farklar vardır. Bu alanlar fark, sınıflar ve veri türleri için parametreler ve dönüş değerleri açığa içerir.  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a> Her iki arabirimi olarak kullanıma sunulan sınıfları ve sınıfları  
 Standart derlemelerde sınıflardan farklı olarak, COM sınıfları birlikte çalışma derlemelerini bir arabirim hem COM sınıfı temsil eden bir sınıf olarak kullanıma sunulur. Arabirim adı, COM sınıfı için aynıdır. Birlikte çalışma sınıfın adını, özgün COM sınıfı aynıdır, ancak "Class" sözcüğüyle eklenir. Örneğin, bir COM nesnesi için bir birlikte çalışma derlemesine bir başvuru içeren bir proje olduğunu varsayalım. COM sınıfı adlandırılmışsa `MyComClass`, IntelliSense ve Nesne Tarayıcısı adlı bir arabirim göster `MyComClass` ve adlı bir sınıf `MyComClassClass`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a> Bir .NET Framework sınıf örneklerini oluşturma  
 Genellikle, örneğini oluşturduğunuz bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kullanarak `New` deyimi ile bir sınıf adı. Birlikte çalışma derlemesi tarafından temsil edilen bir COM sınıfı sahip olduğu kullandığınız bir `New` deyimi bir arabirime sahip. COM sınıfı ile kullanmadığınız sürece bir `Inherits` deyimi, bir sınıf yaptığınız gibi arabirimini kullanabilirsiniz. Aşağıdaki kod nasıl oluşturulacağını gösterir. bir `Command` Microsoft ActiveX veri nesneleri 2.8 kitaplığı COM nesnesine bir başvuru sahip olan bir projeyi nesnesinde:  
  
 [!code-vb[VbVbalrInterop#20](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 Ancak, COM sınıfı türetilmiş bir sınıf için temel olarak kullanıyorsanız, aşağıdaki kodda gösterildiği gibi bir COM sınıfı temsil eden birlikte çalışma sınıfı kullanmanız gerekir:  
  
 [!code-vb[VbVbalrInterop#21](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  Birlikte çalışma bütünleştirilmiş kodları COM sınıfları temsil eden arabirimler örtük olarak uygulayın. Kullanılacak denememelisiniz `Implements` deyimi bu arabirimleri ya da hata uygulamak için neden olur.  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a> Veri türleri için parametreler ve dönüş değerleri  
 Standart derlemeler üyelerinin farklı olarak, özgün nesne bildirimde kullanılan farklı veri türleri birlikte çalışma derlemesi üyeleri olabilir. Birlikte çalışma derlemelerini uyumlu ortak dil çalışma zamanı türleri için örtük olarak COM türlerini dönüştürülse de her iki çalışma zamanı hataları önlemek için kullanılan veri türlerine dikkat. Örneğin, Visual Basic 6.0 ve önceki sürümlerinde, türü değerlerinin oluşturulan COM nesnelerinde `Integer` varsayar [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] eşdeğer türü `Short`. Kullanmadan önce içeri aktarılan üye özellikleri incelemek için Nesne Tarayıcısı kullanmanız önerilir.  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a> Modül düzeyi COM yöntemleri  
 Bir COM sınıfı kullanmanın bir örneğini oluşturarak çoğu COM nesneleri kullanılan `New` anahtar sözcüğü ve ardından nesnenin yöntemleri çağırma. Bu kuralın tek özel durum içeren bir COM nesneleri içerir `AppObj` veya `GlobalMultiUse` COM sınıfları. Bu tür sınıflar, Visual Basic .NET sınıflarını Modül düzeyinde yöntemleri benzer. Örtük olarak Visual Basic 6.0 ve önceki sürümleri bu tür nesnelerin örneklerini, kendi yöntemlerini çağıran ilk kez oluşturun. Örneğin, Visual Basic 6. 0'çağrısı ve Microsoft DAO 3.6 Nesne Kitaplığı için başvuru ekleyebileceğiniz `DBEngine` örneği ilk oluşturmadan yöntemi:  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET, kendi yöntemlerini kullanabilmeniz için önce her zaman COM nesnelerinin örneklerini oluşturmanızı gerektirir. Visual Basic'te bu yöntemi kullanmak için istenen sınıfının bir değişken bildirmek ve nesne nesne değişkenine atamak için new anahtar sözcüğünü kullanın. `Shared` Anahtar sözcüğü emin olmak istediğiniz zaman kullanılabilir sınıf, yalnızca bir örneği oluşturulur.  
  
 [!code-vb[VbVbalrInterop#23](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a> Olay işleyicileri işlenmeyen hatalar  
 Birlikte çalışma yaygın sorunlardan biri, COM nesneleri tarafından oluşturulan olayları işleyen olay işleyicileri hataları içerir. Özellikle kullanarak hataları kontrol sürece bu tür hatalar yoksayılır `On Error` veya `Try...Catch...Finally` deyimleri. Örneğin, aşağıdaki örnekte Microsoft ActiveX veri nesneleri 2.8 kitaplığı COM nesnesine bir başvuru içeren bir Visual Basic .NET projesi arasındadır.  
  
 [!code-vb[VbVbalrInterop#24](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 Bu örnekte, beklendiği gibi bir hata oluşturur. Ancak, aynı örnek olmadan çalışırsanız `Try...Catch...Finally` gibi kullandıysanız bloğu hata yoksayıldı `OnError Resume Next` deyimi. Hata işleme olmadan, sıfıra bölünme sessizce başarısız olur. Bu tür hatalar hiçbir zaman işlenmeyen özel durum hatalarına yükseltmek için özel durum olayları COM nesnelerini işlemek olay işleyicileri'ndeki işleme biçimi kullanmak önemlidir.  
  
### <a name="understanding-com-interop-errors"></a>COM birlikte çalışma hatalarını anlama  
 Hata işleme olmadan, birlikte çalışma çağrıları, genellikle az bilgi sağlayan hatalar oluşturur. Mümkün olduğunda ortaya çıkan sorunlar hakkında daha fazla bilgi sağlamak için yapılandırılmış hata işleme kullanın. Uygulamaların hatalarını ayıklarken bu özellikle yararlı olabilir. Örneğin:  
  
 [!code-vb[VbVbalrInterop#25](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 Özel durum nesnesi içeriğini inceleyerek, hata açıklaması ve HRESULT COM hatalarını kaynağı gibi daha fazla bilgi bulabilirsiniz.  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a> ActiveX denetimi sorunları  
 Visual Basic 6.0 ile çalışan çoğu ActiveX denetimlerini, Visual Basic .NET ile sorun çalışır. Kapsayıcı denetimleri veya görsel olarak diğer denetimleri içeren denetimleri ana özel durumları olan. Visual Studio ile doğru şekilde çalışmaz eski denetimleri bazı örnekleri aşağıdaki gibidir:  
  
-   Microsoft Forms 2.0 çerçeve denetimi  
  
-   Yukarı-Aşağı denetimi olarak da bilinen döndürme denetimi  
  
-   Sheridan sekme denetimi  
  
 Desteklenmeyen ActiveX denetimi sorunları için yalnızca birkaç geçici çözümler vardır. Özgün kaynak kodunun sahibi sizseniz, mevcut denetimleri için Visual Studio geçirebilirsiniz. Aksi takdirde, güncelleştirilmiş yazılım satıcıları ile kontrol edebilirsiniz. NET uyumlu sürümlerini değiştirmek için denetim ActiveX denetimlerini desteklenmiyor.  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a> Salt okunur özelliklerini denetimleri ByRef geçirme  
 Visual Basic .NET geçirdiğinizde COM hataları gibi "Hata 0x800A017F CTL_E_SETNOTSUPPORTED" bazen başlatır `ReadOnly` bazı eski ActiveX denetimlerinin özelliklerini `ByRef` diğer yordamlar için parametreler. Visual Basic 6.0 yordamı çağrılarından benzer bir hata harekete geçirmeyin ve değer olarak geçilemez gibi parametreleri değerlendirilir. Bir özelliğe sahip olmayan bir özellik değiştirmeye çalıştığınız Visual Basic .NET hata iletisi gösterir `Set` yordamı.  
  
 Çağrılan yordama erişiminiz varsa kullanarak bu hatayı önleyebilirsiniz `ByVal` kabul parametreleri bildirmek için anahtar sözcüğü `ReadOnly` özellikleri. Örneğin:  
  
 [!code-vb[VbVbalrInterop#26](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 Çağrılan yordam için kaynak koduna erişim yoksa özelliğini çağıran yordama ayraç fazladan bir dizi ekleyerek değere göre geçirilecek şekilde zorlayabilirsiniz. Örneğin, Microsoft ActiveX veri nesneleri 2.8 kitaplığı COM nesnesine bir başvuru içeren bir proje kullanabilirsiniz:  
  
 [!code-vb[VbVbalrInterop#27](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a> Kullanıma sunan birlikte çalışma derlemeleri dağıtma  
 COM arabirimleri kullanıma derlemeleri dağıtma bazı benzersiz zorluklar teşkil etmektedir. Olası bir sorunu gibi ayrı uygulamalar aynı COM derlemesine başvuru oluşur. Bu durum, bir derlemenin yeni bir sürümü yüklü olduğundan ve başka bir uygulama derleme eski sürümünü kullanmaya devam yaygındır. Bir DLL paylaşan bir derlemeyi kaldırmak, yanlışlıkla, kullanılamayan diğer derlemeler için zorlaştırabilir.  
  
 Bu sorundan kaçınmak için paylaşılan derlemeler genel derleme önbelleği (GAC) yükleyin ve bir MergeModule bileşen için kullanın. Uygulama GAC'de yükleyemezse, bir sürüme özgü alt dizinde Commonfılesfolder için yüklenmelidir.  
  
 Paylaşılmayan derlemeleri yan yana çağıran uygulama dizinde yer almalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Inherits Deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Genel Derleme Önbelleği](../../../framework/app-domains/gac.md)
