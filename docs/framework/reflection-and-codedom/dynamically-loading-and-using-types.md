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
ms.openlocfilehash: 8254d3de7dc282edb8ebe8bf0dd71ce1c943322d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689214"
---
# <a name="dynamically-loading-and-using-types"></a>Dinamik Olarak Yükleme ve Türleri Kullanma
Yansıma, dil derleyiciler tarafından kullanılan altyapı sağlar [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] ve JScript örtük geç bağlama uygulamak için. Bağlama benzersiz olarak belirtilen bir türe karşılık gelen bildirimi (uygulama) bulma işlemidir. Bu işlem, çalışma zamanında değil derleme zamanında oluştuğunda, geç bağlama olarak adlandırılır. [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] örtük geç bağlama kodunuzda kullanmanıza olanak tanır; Visual Basic Derleyicisi, nesnenin türü elde etmek için yansıma kullanan bir yardımcı yöntem çağırır. Yardımcı yöntemine geçirilen bağımsız değişkenler, çalışma zamanında çağrılacak uygun yöntemi neden. Bu bağımsız değişkenler (nesne) örneği yöntemi, çağrılan yöntemi (dize) ve çağrılan yöntemi (nesne dizisini) geçirilen bağımsız değişkenler adını çağırmak için açıktır.  
  
 Aşağıdaki örnekte, Visual Basic Derleyicisi yansıma örtük olarak türü derleme zamanında bilinen değil bir nesne üzerinde bir yöntemi çağırmak için kullanır. A **HelloWorld** sınıfında bir **PrintHello** "Hello geçirilir bazı metin ile birleştirilmiş World" out yazdırır yöntemi **PrintHello** yöntemi. **PrintHello** Bu örnekte adlı bir yöntem olan aslında bir <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>; Visual Basic kodunu verir **PrintHello** (helloObj) nesne türü derleme biliniyorsa olarak çağrılacak yöntemi saat (erken bağlama) yerine, çalışma zamanı (geç bağlama).  
  
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
 Derleyiciler tarafından geç bağlama için örtük olarak kullanılan ek olarak, yansıma açıkça kodda geç bağlama gerçekleştirmek için kullanılabilir.  
  
 [Ortak dil çalışma zamanı](../../../docs/standard/clr.md) birden fazla programlama dili ve bağlama kurallarını bu dillerden farklı destekler. Erken bağlı durumda kod oluşturucuları, bu bağlama tamamen denetleyebilirsiniz. Bununla birlikte, yansıma yoluyla geç bağlama içinde bağlama özelleştirilmiş bağlama tarafından denetlenebilir. <xref:System.Reflection.Binder> Seçimi ve çağırma üyesi özel denetim sınıf sağlar.  
  
 Özel bağlama kullanma, çalışma zamanında bir derlemeyi yüklemek, derleme, istediğiniz türünü belirtin ve ardından yöntemleri veya erişim alan ya da bu tür özelliklerde çağırma türleri hakkında bilgi alın. Nesne türü kullanıcı girdisi bağımlı olduğunda gibi derleme zamanında, nesnenin türünü bilmiyorsanız bu teknik yararlıdır.  
  
 Aşağıdaki örnek, bağımsız değişken türü dönüştürme sağlayan basit bir özel bağlayıcı gösterir. İçin kod `Simple_Type.dll` ana örnek önce gelir. Derleme mutlaka `Simple_Type.dll` ve buna bir başvuru projede oluşturma zamanında ardından ekleyin.  
  
 [!code-cpp[Conceptual.Types.Dynamic#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.Dynamic#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.Dynamic#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source1.vb#1)]  
  
### <a name="invokemember-and-createinstance"></a>InvokeMember ve CreateInstance  
 Kullanım <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType> bir tür üyesi çağrılamadı. **CreateInstance** gibi çeşitli yöntemleri sınıfları <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> ve <xref:System.Reflection.Assembly.CreateInstance%2A?displayProperty=nameWithType>, özelleştirilmiş formlar, **InvokeMember** belirtilen türün yeni örneğini oluşturur. **Bağlayıcı** sınıfı, bu yöntemler aşırı yükleme çözümlemesi ve bağımsız değişken zorlama için kullanılır.  
  
 Aşağıdaki örnek, üç olası eşleştirme birleşimlerini bağımsız değişken zorlama (tür dönüştürme) ve üye seçimi gösterir. Durum 1'de, bağımsız değişken zorlama veya üye seçimi gereklidir. Durum 2'de, yalnızca üye seçimi gereklidir. Durum 3'te yalnızca bağımsız değişken zorlama gereklidir.  
  
 [!code-cpp[Conceptual.Types.Dynamic#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.Dynamic#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.Dynamic#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source2.vb#2)]  
  
 Aynı ada sahip birden fazla üye kullanılabilir olduğunda aşırı yükleme çözünürlüğü gereklidir. <xref:System.Reflection.Binder.BindToMethod%2A?displayProperty=nameWithType> Ve <xref:System.Reflection.Binder.BindToField%2A?displayProperty=nameWithType> yöntemleri bağlama için tek bir üye çözmek için kullanılır. **Binder.BindToMethod** ayrıca özelliği çözümlemesi sağlar **alma** ve **ayarlamak** özellik erişimcileri.  
  
 **BindToMethod** döndürür <xref:System.Reflection.MethodBase> çağırmak için veya bir null başvuru (**hiçbir şey** Visual Basic'te) gibi bir çağrı mümkün değilse. **MethodBase** dönüş değeri olması gerekmez bunların içerdiği *eşleşen* parametresi rağmen normal bir durumdur.  
  
 ByRef bağımsız değişken mevcut olduğunda, çağırana geri dönmek isteyebilirsiniz. Bu nedenle, **bağlayıcı** sağlar, bağımsız değişken dizisi özgün biçimlerinde eşlemek bir istemci **BindToMethod** bağımsız değişken dizisi yönetilen. Bunu yapmak için çağırana bağımsız değişkenlerin sırası değiştirilmemiş olduğunu garanti gerekir. Bağımsız değişken adıyla geçirildiğinde **bağlayıcı** bağımsız değişken dizisi ve diğer bir deyişle ne çağıran görür yeniden sıralar. Daha fazla bilgi için bkz. <xref:System.Reflection.Binder.ReorderArgumentArray%2A?displayProperty=nameWithType>.  
  
 Kullanılabilir üyeler kümesidir türde veya herhangi bir taban türü içinde tanımlanan bu üyeler. Varsa <xref:System.Reflection.BindingFlags> belirtilirse, kümedeki tüm erişilebilirlik üyeleri döndürülür. Varsa **BindingFlags.NonPublic** belirtilmezse, bağlayıcı erişilebilirlik kuralları zorlamalıdır. Belirtirken **genel** veya **özel** bağlama bayrağı da belirtmeniz gerekir **örneği** veya **statik** bayrağı veya Hayır'ı bağlama üyeleri döndürülür.  
  
 Verilen ad yalnızca bir üyesi ise, hiçbir geri çağırma gereklidir ve bağlama üzerinde bu yöntem gerçekleştirilir. 1. durum kod örneği, bu noktayı gösterir: Yalnızca bir **PrintBob** yöntemi vardır ve bu nedenle hiçbir geri çağırma gereklidir.  
  
 Kullanılabilirlik kümesi içinde birden fazla üyesi ise, tüm bu yöntemleri geçirilen **BindToMethod**, uygun yöntemi seçer ve döndürür. Kod örneği, servis talebi 2'de adlı iki yöntem vardır **PrintValue**. Uygun yöntemi çağırarak seçili **BindToMethod**.  
  
 <xref:System.Reflection.Binder.ChangeType%2A> Seçilen yöntemi biçimsel bağımsız değişkenleri türüne dönüştüren gerçek bağımsız değişken, bağımsız değişken zorlama (tür dönüştürme) gerçekleştirir. **ChangeType** bile türleri tam olarak eşleşmesi için her bir bağımsız değişken olarak adlandırılır.  
  
 Kod örneği, gerçek bağımsız değişken türü'nın çalışması 3'te **dize** "5.5" değeri olan bir biçimsel bağımsız değişken türü olan bir yönteme geçirilen **çift**. Çağrı başarılı olması "5.5" dize değeri çift değerine dönüştürülmesi gerekir. **ChangeType** bu dönüştürmeyi gerçekleştirir.  
  
 **ChangeType** yalnızca kayıpsız gerçekleştirir veya [zorlamayı genişletme](../../../docs/standard/base-types/type-conversion.md)aşağıdaki tabloda gösterildiği gibi.  
  
|Kaynak türü|Hedef türü|  
|-----------------|-----------------|  
|Herhangi bir türü|Kendi temel türü|  
|Herhangi bir türü|Implements arabirimi|  
|Char|Uınt16, Uınt32, Int32, UInt64, Int64, tek bir, iki|  
|Bayt|Char, Uınt16, Int16, Uınt32, Int32, UInt64, Int64, tek, Double|  
|SByte|Int16, Int32, Int64, tek bir, iki|  
|UInt16|Uınt32, Int32, UInt64, Int64, tek bir, iki|  
|Int16|Int32, Int64, tek bir, iki|  
|UInt32|UInt64, Int64, tek bir, iki|  
|Int32|Int64, tek ve çift|  
|UInt64|Tek, Double|  
|Int64|Tek, Double|  
|Tek|Çift|  
|Nonreference türü|Başvuru türü|  
  
 <xref:System.Type> Sınıfında **alma** tür parametreleri kullanan yöntemler **bağlayıcı** belirli bir üye başvurularını çözümlemek için. <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType>, <xref:System.Type.GetMethod%2A?displayProperty=nameWithType>, ve <xref:System.Type.GetProperty%2A?displayProperty=nameWithType> belirli üye bu üyenin imzası bilgileri sağlayarak geçerli türden arayın. <xref:System.Reflection.Binder.SelectMethod%2A?displayProperty=nameWithType> ve <xref:System.Reflection.Binder.SelectProperty%2A?displayProperty=nameWithType> geri uygun yöntemleri verilen imza bilgilerini seçin açın olarak da adlandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- [Tür Bilgilerini Görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [.NET Framework'te tür dönüştürme](../../../docs/standard/base-types/type-conversion.md)
