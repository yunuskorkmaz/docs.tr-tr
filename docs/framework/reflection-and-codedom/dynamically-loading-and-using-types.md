---
title: Dinamik Olarak Yükleme ve Türleri Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- late binding, about late binding
- early binding
- dynamically loading and using types
- implicit late binding
- reflection, dynamically using types
ms.assetid: db985bec-5942-40ec-b13a-771ae98623dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0246f429b396a2606bbb827b7ae2a9034af00f11
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915471"
---
# <a name="dynamically-loading-and-using-types"></a>Dinamik Olarak Yükleme ve Türleri Kullanma
Yansıma, örtülü geç bağlamayı uygulamak için dil derleyicileri tarafından kullanılan altyapıyı sağlar. Bağlama, benzersiz olarak belirtilen bir türe karşılık gelen bildirimi (yani, uygulama) bulma işlemidir. Bu işlem, derleme süresi yerine çalışma zamanında gerçekleştiğinde, geç bağlama olarak adlandırılır. Visual Basic kodunuzda örtük geç bağlamayı kullanmanıza izin verir; Visual Basic derleyici, nesne türünü almak için yansıma kullanan bir yardımcı yöntemi çağırır. Yardımcı yöntemine geçirilen bağımsız değişkenler, uygun yöntemin çalışma zamanında çağrılmasına neden olur. Bu bağımsız değişkenler, yöntemi çağırmak için gereken örnek (bir nesne), çağrılan metodun adı (bir dize) ve çağrılan yönteme geçirilen bağımsız değişkenler (bir nesne dizisi).  
  
 Aşağıdaki örnekte Visual Basic Derleyicisi, türü derleme sırasında bilinmeyen bir nesne üzerinde bir yöntemi çağırmak için yansımayı örtük olarak kullanır. **HelloWorld** sınıfının, **PrintHello** yöntemine geçirilen bazı metinler ile birleştirilmiş "Merhaba Dünya" yazdıran bir **PrintHello** yöntemi vardır. Bu örnekte çağrılan **PrintHello** yöntemi aslında bir <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>örnektir; Visual Basic kodu, nesne türü (HelloObj), çalışma zamanı yerine derleme zamanı (erken bağlama) olarak bilinmiş gibi, **PrintHello** yönteminin çağrılmasını sağlar ( geç bağlama).  
  
```  
Imports System  
Module Hello  
    Sub Main()  
        ' Sets up the variable.  
        Dim helloObj As Object  
        ' Creates the object.  
        helloObj = new HelloWorld()  
        ' Invokes the print method as if it was early bound  
        ' even though it is really late bound.  
        helloObj.PrintHello("Visual Basic Late Bound")  
    End Sub  
End Module  
```  
  
## <a name="custom-binding"></a>Özel Bağlama  
 En geç bağlama için derleyiciler tarafından örtük olarak kullanılmanın yanı sıra, yansıma, geç bağlamayı gerçekleştirmek için doğrudan kodda kullanılabilir.  
  
 [Ortak dil çalışma zamanı](../../standard/clr.md) birden çok programlama dilini destekler ve bu dillerin bağlama kuralları farklılık gösterir. Erken bağlantılı durumda, kod oluşturucuları bu bağlamayı tamamen denetleyebilir. Ancak, yansıma aracılığıyla geç bağlamada bağlama özelleştirilmiş bağlama tarafından denetlenmelidir. Sınıfı <xref:System.Reflection.Binder> , üye seçimi ve çağırma için özel denetim sağlar.  
  
 Özel bağlama kullanarak, çalışma zamanında bir derleme yükleyebilir, bu derlemedeki türler hakkında bilgi alabilir, istediğiniz türü belirtebilir ve ardından Yöntemler veya erişim alanları ya da bu tür üzerinde Özellikler çalıştırabilirsiniz. Bu teknik, nesne türünün Kullanıcı girişine bağlı olduğu durumlarda olduğu gibi, derleme zamanında bir nesnenin türünü tanımadığınız durumlarda faydalıdır.  
  
 Aşağıdaki örnek, bağımsız değişken türü dönüştürmesi sağlayan basit bir özel cildi gösterir. Kod, ana örneğin önünegelir.`Simple_Type.dll` Derleme zamanında projede buna `Simple_Type.dll` bir başvuru oluşturup eklediğinizden emin olun.  
  
 [!code-cpp[Conceptual.Types.Dynamic#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.Dynamic#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.Dynamic#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source1.vb#1)]  
  
### <a name="invokemember-and-createinstance"></a>InvokeMember ve CreateInstance  
 Bir <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType> türün üyesini çağırmak için kullanın. <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> Ve gibi<xref:System.Reflection.Assembly.CreateInstance%2A?displayProperty=nameWithType>çeşitli sınıfların CreateInstance yöntemleri, belirtilen türde yeni örnekler oluşturan **InvokeMember** 'ın özelleştirilmiş formlarıdır. **Ciltçi** sınıfı, bu yöntemlerde aşırı yükleme çözümü ve bağımsız değişken zorlaması için kullanılır.  
  
 Aşağıdaki örnek, bağımsız değişken zorlaması (tür dönüştürme) ve üye seçimi için olası üç kombinasyonu gösterir. 1\. durumda, bağımsız değişken zorlaması veya üye seçimi gerekli değildir. 2\. durumda, yalnızca üye seçimi gereklidir. 3\. durumda, yalnızca bağımsız değişken zorlaması gerekir.  
  
 [!code-cpp[Conceptual.Types.Dynamic#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.Dynamic#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.Dynamic#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source2.vb#2)]  
  
 Aynı ada sahip birden fazla üye varsa aşırı yükleme çözümlemesi gerekir. <xref:System.Reflection.Binder.BindToMethod%2A?displayProperty=nameWithType> Ve<xref:System.Reflection.Binder.BindToField%2A?displayProperty=nameWithType> yöntemleri, tek bir üyeye bağlamayı çözümlemek için kullanılır. **Ciltçi. BindToMethod** Ayrıca **Get** ve **set** özelliği erişimcileri aracılığıyla Özellik çözümlemesi sağlar.  
  
 **BindToMethod** , <xref:System.Reflection.MethodBase> böyle bir çağrı mümkün değilse Invoke veya null başvurusu (Visual Basic**hiçbir şey** ) döndürür. **MethodBase** dönüş değeri, *eşleşme* parametresinde yer alan öğelerden biri olmalıdır, ancak bu durum olağan durumdur.  
  
 ByRef bağımsız değişkenleri mevcut olduğunda, çağıran bunları geri almak isteyebilir. Bu nedenle, **bağlayıcı** , **BindToMethod** bağımsız değişken dizisini işlese, bir istemcinin bağımsız değişken dizisini özgün biçimine geri eşlemesini sağlar. Bunu yapmak için, çağıran bağımsız değişkenlerin sırasının değiştirilmemiş olması garanti etmelidir. Bağımsız değişkenler ad ile geçirildiğinde, **Ciltçi** bağımsız değişken dizisini yeniden sıralar ve çağıranın gördüğü şeydir. Daha fazla bilgi için bkz. <xref:System.Reflection.Binder.ReorderArgumentArray%2A?displayProperty=nameWithType>.  
  
 Kullanılabilir Üyeler kümesi, tür veya herhangi bir temel tür içinde tanımlanan üyeleridir. <xref:System.Reflection.BindingFlags> Belirtilmişse, herhangi bir erişilebilirliğin üyeleri bu küme içinde döndürülür. **BindingFlags. ortak** belirtilmemişse, bağlayıcı erişilebilirlik kurallarını zorlayamalıdır. **Genel veya ortak** bağlama bayrağını belirtirken, **örneği** veya **statik** bağlama bayrağını da belirtmeniz veya hiçbir üyenin döndürülmeyeceğini belirtmeniz gerekir.  
  
 Verilen adın yalnızca bir üyesi varsa, hiçbir geri çağrı gerekmez ve bağlama Bu yöntemde yapılır. Kod örneğinin 1. durumu bu noktayı gösterir: Yalnızca bir **PrintBob** yöntemi kullanılabilir ve bu nedenle hiçbir geri arama gerekmez.  
  
 Kullanılabilir küme içinde birden fazla üye varsa, bu yöntemlerin hepsi, uygun yöntemi seçen ve döndüren **BindToMethod**'a geçirilir. Kod örneğinin 2. durumda, **PrintValue**adlı iki yöntem vardır. **BindToMethod**çağrısıyla ilgili Yöntem seçilidir.  
  
 <xref:System.Reflection.Binder.ChangeType%2A>gerçek bağımsız değişkenleri seçili metodun biçimsel bağımsız değişkenlerinin türüne dönüştüren bağımsız değişken zorlaması (tür dönüştürme) gerçekleştirir. Türler tam olarak eşleşiyorsa bile her bağımsız değişken için **ChangeType** çağrılır.  
  
 Kod örneğinin 3. durumunda, "5,5" değerine sahip **dize** türünde gerçek bir bağımsız değişken, **Double**türünde bir biçimsel bağımsız değişkene sahip bir yönteme geçirilir. Çağrının başarılı olması için, "5,5" dize değerinin bir Double değere dönüştürülmesi gerekir. **ChangeType** bu dönüştürmeyi gerçekleştirir.  
  
 **ChangeType** , aşağıdaki tabloda gösterildiği gibi yalnızca kayıpsız veya [genişleyen zorlamalar](../../standard/base-types/type-conversion.md)gerçekleştirir.  
  
|Kaynak türü|Hedef türü|  
|-----------------|-----------------|  
|Herhangi bir tür|Temel türü|  
|Herhangi bir tür|Uyguladığı arabirim|  
|Char|UInt16, UInt32, Int32, UInt64, Int64, Single, Double|  
|Bayt|Char, UInt16, Int16, UInt32, Int32, UInt64, Int64, Single, Double|  
|SByte|Int16, Int32, Int64, Single, Double|  
|UInt16|UInt32, Int32, UInt64, Int64, Single, Double|  
|Int16|Int32, Int64, Single, Double|  
|UInt32|UInt64, Int64, Single, Double|  
|Int32|Int64, Single, Double|  
|UInt64|Tek, Çift|  
|Int64|Tek, Çift|  
|Tek|Çift|  
|Başvuru olmayan tür|Başvuru türü|  
  
 Sınıfı <xref:System.Type> , belirli bir üyeye yönelik başvuruları çözümlemek için **bağlayıcı** türünde parametreler kullanan **Get** yöntemlerine sahiptir. <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType>, <xref:System.Type.GetMethod%2A?displayProperty=nameWithType> ve<xref:System.Type.GetProperty%2A?displayProperty=nameWithType> Bu üyeye ait imza bilgilerini sağlayarak geçerli türün belirli bir üyesini arayın. <xref:System.Reflection.Binder.SelectMethod%2A?displayProperty=nameWithType>ve <xref:System.Reflection.Binder.SelectProperty%2A?displayProperty=nameWithType> uygun yöntemlerin verilen imza bilgilerini seçmek için geri çağırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- [Tür Bilgilerini Görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [.NET Framework dönüştürme türü](../../standard/base-types/type-conversion.md)
