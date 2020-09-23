---
title: Birlikte Çalışabilirlik İle İlgili Sorun Giderme
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
ms.openlocfilehash: 135b121638b92adc5a3b0920aa29d10fd1d62d14
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075999"
---
# <a name="troubleshooting-interoperability-visual-basic"></a>Birlikte Çalışabilirlik İle İlgili Sorun Giderme (Visual Basic)

.NET Framework COM ile yönetilen kod arasında birlikte çalışırken, aşağıdaki yaygın sorunlardan biri veya birkaçı olabilir.  
  
## <a name="interop-marshaling"></a><a name="vbconinteroperabilitymarshalinganchor1"></a> Birlikte çalışabilirlik sıralaması  

 Her zaman, .NET Framework parçası olmayan veri türlerini kullanmanız gerekebilir. Birlikte çalışma derlemeleri, COM nesneleri için çalışmanın çoğunu işler, ancak yönetilen nesneler COM 'a sunulduğunda kullanılan veri türlerini kontrol etmeniz gerekebilir. Örneğin, sınıf kitaplıklarındaki yapılar, `BStr` Visual Basic 6,0 ve önceki sürümlerde oluşturulan com nesnelerine gönderilen dizelerde yönetilmeyen türü belirtmelidir. Bu gibi durumlarda, <xref:System.Runtime.InteropServices.MarshalAsAttribute> Yönetilen türlerin yönetilmeyen türler olarak gösterilmesini sağlamak için özniteliğini kullanabilirsiniz.  
  
## <a name="exporting-fixed-length-strings-to-unmanaged-code"></a><a name="vbconinteroperabilitymarshalinganchor2"></a> Sabit uzunluklu dizeleri yönetilmeyen koda verme  

 Visual Basic 6,0 ve önceki sürümlerde dizeler, COM nesnelerine null sonlandırma karakteri olmayan bayt dizileri olarak aktarılmalıdır. Diğer dillerle uyumluluk için, .NET Visual Basic dizeleri dışarı aktarırken sonlandırma karakteri içerir. Bu uyumsuzluğun en iyi yolu, sonlandırma karakteri olmayan dizeleri veya dizileri olarak dışa aktarmak `Byte` `Char` .  
  
## <a name="exporting-inheritance-hierarchies"></a><a name="vbconinteroperabilitymarshalinganchor3"></a> Devralma hiyerarşileri dışarı aktarılıyor  

 Yönetilen sınıf hiyerarşileri, COM nesneleri olarak sunulduğunu düzleştirebilir. Örneğin, bir üye içeren bir temel sınıf tanımlarsanız ve sonra bir COM nesnesi olarak sunulan türetilmiş bir sınıfta temel sınıfı devraldıysanız, COM nesnesinde türetilmiş sınıfı kullanan istemciler devralınan üyeleri kullanamaz. Temel sınıf üyelerine yalnızca bir temel sınıfın örnekleri olarak COM nesnelerinden erişilebilir ve ardından yalnızca temel sınıf de bir COM nesnesi olarak oluşturulur.  
  
## <a name="overloaded-methods"></a>Aşırı Yüklenmiş Yöntemler  

 Visual Basic aşırı yüklenmiş yöntemler oluşturabilseniz de, COM tarafından desteklenmez. Aşırı yüklenmiş yöntemler içeren bir sınıf bir COM nesnesi olarak kullanıma sunulduğunda, aşırı yüklenmiş yöntemler için yeni yöntem adları oluşturulur.  
  
 Örneğin, yöntemin iki aşırı yüküne sahip bir sınıfı düşünün `Synch` . Sınıf bir COM nesnesi olarak kullanıma sunulduğunda, yeni oluşturulan yöntem adları `Synch` ve olabilir `Synch_2` .  
  
 Yeniden adlandırma, COM nesnesinin tüketicileri için iki soruna neden olabilir.  
  
1. İstemciler oluşturulan yöntem adlarını beklememeyebilir.  
  
2. Bir COM nesnesi olarak sunulan sınıfta oluşturulan yöntem adları, sınıfa veya temel sınıfına yeni aşırı yüklemeler eklendiğinde değişebilir. Bu, sürüm oluşturma sorunlarına neden olabilir.  
  
 Her iki sorunu da çözümlemek için, COM nesneleri olarak kullanıma sunulacak nesneleri geliştirirken, her yönteme, aşırı yükleme kullanmak yerine benzersiz bir ad verin.  
  
## <a name="use-of-com-objects-through-interop-assemblies"></a><a name="vbconinteroperabilitymarshalinganchor4"></a> Birlikte çalışma derlemeleri aracılığıyla COM nesnelerinin kullanımı  

 Birlikte çalışma derlemelerini, temsil ettikleri COM nesneleri için yönetilen kod değiştirmeleri gibi neredeyse kullanırsınız. Ancak, sarmalayıcılar olduklarından ve gerçek COM nesneleri olmadığından, birlikte çalışma derlemeleri ve standart derlemelerin kullanılması arasında bazı farklılıklar vardır. Bu fark alanlarında sınıfların pozlaması ve parametreler ve dönüş değerleri için veri türleri yer alır.  
  
## <a name="classes-exposed-as-both-interfaces-and-classes"></a><a name="vbconinteroperabilitymarshalinganchor5"></a> Hem arabirimler hem de sınıflar olarak gösterilen sınıflar  

 Standart derlemelerdeki sınıfların aksine COM sınıfları, birlikte çalışma derlemelerindeki bir arabirim ve COM sınıfını temsil eden bir sınıf olarak sunulur. Arabirimin adı, COM sınıfıyla aynıdır. Birlikte çalışma sınıfının adı, özgün COM sınıfının, ancak "Class" sözcüğünün eklendiği ile aynıdır. Örneğin, bir COM nesnesi için birlikte çalışma derlemesine başvuru içeren bir projeniz olduğunu varsayalım. COM sınıfı adlandırılmışsa `MyComClass` , IntelliSense ve nesne tarayıcısı adlı bir arabirimi `MyComClass` ve adlı bir sınıfı gösterir `MyComClassClass` .  
  
## <a name="creating-instances-of-a-net-framework-class"></a><a name="vbconinteroperabilitymarshalinganchor6"></a> .NET Framework sınıfının örneklerini oluşturma  

 Genellikle, `New` sınıf adı olan ifadesini kullanarak bir .NET Framework sınıfının örneğini oluşturursunuz. Bir birlikte çalışma derlemesi tarafından temsil edilen COM sınıfının olması, bu `New` ifadeyi bir arabirimiyle kullanabileceğiniz bir durumdur. COM sınıfını bir ifadesiyle kullanmadığınız sürece `Inherits` , arabirimi tıpkı bir sınıf gibi kullanabilirsiniz. Aşağıdaki kod, bir `Command` projede Microsoft ActiveX Data Objects 2,8 LIBRARY com nesnesine yönelik bir başvuruya sahip bir nesne oluşturmayı gösterir:  
  
 [!code-vb[VbVbalrInterop#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#20)]  
  
 Ancak, bir türetilmiş sınıf için temel olarak COM sınıfını kullanıyorsanız, aşağıdaki kodda olduğu gibi COM sınıfını temsil eden birlikte çalışma sınıfını kullanmanız gerekir:  
  
 [!code-vb[VbVbalrInterop#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#21)]  
  
> [!NOTE]
> Birlikte çalışma derlemeleri, COM sınıflarını temsil eden arabirimleri örtülü olarak uygular. `Implements`Bu arabirimleri uygulamak için ifadesini kullanmayı denememelisiniz veya bir hata ortaya kalacak.  
  
## <a name="data-types-for-parameters-and-return-values"></a><a name="vbconinteroperabilitymarshalinganchor7"></a> Parametreler ve dönüş değerleri için veri türleri  

 Standart derlemelerin üyelerinin aksine, birlikte çalışma derleme üyeleri özgün nesne bildiriminde kullanılanlardan farklı veri türlerine sahip olabilir. Birlikte çalışma derlemeleri dolaylı olarak COM türlerini uyumlu ortak dil çalışma zamanı türlerine dönüştürse de, çalışma zamanı hatalarını engellemek için her iki taraf tarafından kullanılan veri türlerine dikkat etmeniz gerekir. Örneğin, Visual Basic 6,0 ve önceki sürümlerde oluşturulan COM nesnelerinde, tür değerleri `Integer` .NET Framework denk türü varsayar `Short` . İçeri aktarılan üyelerin özelliklerini kullanmadan önce incelemek için Nesne Tarayıcısı kullanmanız önerilir.  
  
## <a name="module-level-com-methods"></a><a name="vbconinteroperabilitymarshalinganchor8"></a> Modül düzeyi COM yöntemleri  

 Çoğu COM nesnesi, anahtar sözcüğünü kullanarak COM sınıfının bir örneğini oluşturarak `New` ve sonra nesnenin yöntemlerini çağırarak kullanılır. Bu kural için bir özel durum, `AppObj` veya com sınıfları IÇEREN com nesnelerini içerir `GlobalMultiUse` . Bu sınıflar, Visual Basic .NET sınıflarında modül düzeyi yöntemlere benzer. Visual Basic 6,0 ve önceki sürümler, yöntemlerinden birini ilk kez çağırdığınızda bu nesnelerin örneklerini örtülü olarak oluşturur. Örneğin, Visual Basic 6,0 ' de, Microsoft DAO 3,6 nesne kitaplığına bir başvuru ekleyebilir ve `DBEngine` öncelikle bir örnek oluşturmadan yöntemi çağırabilirsiniz:  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET, yöntemlerini kullanabilmeniz için her zaman COM nesneleri örnekleri oluşturmanızı gerektirir. Bu yöntemleri Visual Basic ' de kullanmak için, istenen sınıfın bir değişkenini bildirin ve yeni anahtar sözcüğünü kullanarak nesneyi nesne değişkenine atayın. `Shared`Anahtar sözcüğü, sınıfın yalnızca bir örneğinin oluşturulduğundan emin olmak istediğinizde kullanılabilir.  
  
 [!code-vb[VbVbalrInterop#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#23)]  
  
## <a name="unhandled-errors-in-event-handlers"></a><a name="vbconinteroperabilitymarshalinganchor9"></a> Olay Işleyicilerde işlenmeyen hatalar  

 Ortak bir birlikte çalışma sorunu, COM nesneleri tarafından oluşturulan olayları işleyen olay işleyicilerindeki hataları içerir. Bu tür hatalar, veya deyimlerini kullanarak hataları özellikle denetmediğiniz takdirde yok sayılır `On Error` `Try...Catch...Finally` . Örneğin, aşağıdaki örnek, Microsoft ActiveX Data Objects 2,8 Library COM nesnesine yönelik bir başvuruya sahip Visual Basic bir .NET projesinden verilmiştir.  
  
 [!code-vb[VbVbalrInterop#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#24)]  
  
 Bu örnek, beklenen şekilde bir hata oluşturur. Ancak, blok olmadan aynı örneği denerseniz `Try...Catch...Finally` , hata, ifadesini kullanmış gibi yok sayılır `OnError Resume Next` . Hata işleme olmadan, sıfıra kadar bölme sessizce başarısız olur. Bu tür hatalar hiçbir şekilde işlenmemiş özel durum hatalarını yükseltmediği için, COM nesnelerinden olayları işleyen olay işleyicilerinde özel durum işlemenin bir biçimini kullanmanız önemlidir.  
  
### <a name="understanding-com-interop-errors"></a>COM birlikte çalışma hatalarını anlama  

 Hata işleme olmadan, birlikte çalışma çağrıları genellikle az bilgi sağlayan hatalar oluşturur. Mümkün olduğunda, oluşma sorunları hakkında daha fazla bilgi sağlamak için yapılandırılmış hata işlemeyi kullanın. Bu, özellikle uygulamalarda hata ayıklarken yararlı olabilir. Örneğin:  
  
 [!code-vb[VbVbalrInterop#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#25)]  
  
 Özel durum nesnesinin içeriğini inceleyerek hata açıklaması, HRESULT ve COM hatalarının kaynağı gibi bilgileri bulabilirsiniz.  
  
## <a name="activex-control-issues"></a><a name="vbconinteroperabilitymarshalinganchor10"></a> ActiveX denetim sorunları  

 Visual Basic 6,0 ile çalışan çoğu ActiveX denetimleri, sorun olmaksızın Visual Basic .NET ile çalışır. Ana özel durumlar, kapsayıcı denetimleridir veya görsel olarak diğer denetimleri içeren denetimlerdir. Visual Studio ile düzgün çalışmayan eski denetimlerin bazı örnekleri şunlardır:  
  
- Microsoft Forms 2,0 çerçeve denetimi  
  
- Aşağı açılan denetim, döndürme denetimi olarak da bilinir  
  
- Sheridan Tab denetimi  
  
 Desteklenmeyen ActiveX denetim sorunları için yalnızca birkaç geçici çözüm vardır. Özgün kaynak koda sahipseniz, varolan denetimleri Visual Studio 'ya geçirebilirsiniz. Aksi takdirde, yazılım satıcılarıyla güncelleştirilmiş olup olmadığını kontrol edebilirsiniz. Desteklenmeyen ActiveX denetimlerinin yerini alacak denetimlerin NET uyumlu sürümleri.  
  
## <a name="passing-readonly-properties-of-controls-byref"></a><a name="vbconinteroperabilitymarshalinganchor11"></a> Denetimlerin ReadOnly özelliklerinin geçirilmesi ByRef  

 `ReadOnly`Bazı eski ActiveX denetimlerinin özelliklerini diğer yordamlara parametre olarak geçirdiğinizde, .net Visual Basic bazen "hata 0x800A017F CTL_E_SETNOTSUPPORTED" gıbı com hataları oluşturur `ByRef` . Visual Basic 6,0 ' den benzer yordam çağrıları bir hata oluşturmaz ve parametreleri değere göre geçirmiş gibi kabul edilir. Visual Basic .NET hata iletisi, özellik yordamı olmayan bir özelliği değiştirmeye çalıştığınız anlamına gelir `Set` .  
  
 Çağrılan yordama erişiminiz varsa, `ByVal` özellikleri kabul eden parametreleri bildirmek için anahtar sözcüğünü kullanarak bu hatayı önleyebilirsiniz `ReadOnly` . Örneğin:  
  
 [!code-vb[VbVbalrInterop#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#26)]  
  
 Çağrılmakta olan yordamın kaynak koduna erişiminiz yoksa, çağıran yordamın çevresine fazladan bir parantez kümesi ekleyerek özelliği değere göre geçirilecek şekilde zorlayabilirsiniz. Örneğin, Microsoft ActiveX Data Objects 2,8 Library COM nesnesine bir başvuru içeren bir projede şunları kullanabilirsiniz:  
  
 [!code-vb[VbVbalrInterop#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#27)]  
  
## <a name="deploying-assemblies-that-expose-interop"></a><a name="vbconinteroperabilitymarshalinganchor12"></a> Birlikte çalışabilirliği sunan derlemeleri dağıtma  

 COM arabirimlerini sunan derlemelerin dağıtımı bazı benzersiz güçlükler sunar. Örneğin, ayrı uygulamalar aynı COM derlemesine başvuru yaparken olası bir sorun oluşur. Bu durum, bir derlemenin yeni bir sürümü yüklendiğinde ve başka bir uygulamanın derlemenin eski sürümünü kullanmaya devam ediyorsa yaygın bir durumdur. DLL 'yi paylaşan bir derlemeyi kaldırırsanız, yanlışlıkla diğer derlemeler için kullanılamaz hale getirebilirsiniz.  
  
 Bu sorundan kaçınmak için, paylaşılan derlemeleri genel derleme önbelleği 'ne (GAC) yüklemeli ve bileşen için bir MergeModule kullanmalısınız. Uygulamayı GAC 'ye yükleyemezseniz, sürüme özgü bir alt dizinde Commonfilesklasörüne yüklenmelidir.  
  
 Paylaşılmayan derlemeler, çağıran uygulamayla birlikte dizinde yan yana yerleştirilmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [COM birlikte çalışma](index.md)
- [Tlbimp.exe (tür kitaplığı Içeri Aktarıcı)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (tür kitaplığı verme programı)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama](walkthrough-implementing-inheritance-with-com-objects.md)
- [Inherits Deyimi](../../language-reference/statements/inherits-statement.md)
- [Genel Derleme Önbelleği](../../../framework/app-domains/gac.md)
