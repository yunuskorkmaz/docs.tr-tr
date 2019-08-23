---
title: Using Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 346a26ad5751599831d8b0d3e0497e4d488eb76c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957541"
---
# <a name="using-statement-visual-basic"></a>Using Deyimi (Visual Basic)
Bir `Using` bloğun başlangıcını bildirir ve isteğe bağlı olarak, blok denetimlerinin bulunduğu sistem kaynaklarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`resourcelist`|Belirtmezseniz gereklidir `resourceexpression`. Bu `Using` blok tarafından denetimlerin, virgülle ayrılmış bir veya daha fazla sistem kaynağı listesi.|  
|`resourceexpression`|Belirtmezseniz gereklidir `resourcelist`. Bu `Using` blok tarafından denetlenebilecek bir sistem kaynağına başvuran başvuru değişkeni veya ifadesi.|  
|`statements`|İsteğe bağlı. `Using` Bloğun çalıştığı deyimler bloğu.|  
|`End Using`|Gerekli. , Denetlediği tüm kaynakların `Using` bloğunun ve ayırdığından oluşan tanımı sonlandırır.|  
  
 `resourcelist` Parçasındaki her kaynak aşağıdaki söz dizimi ve bölümlere sahiptir:  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 -veya-  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourceList bölümleri  
  
|Terim|Tanım|  
|---|---|  
|`resourcename`|Gerekli. `Using` Blok denetimlerinin bulunduğu bir sistem kaynağına başvuran başvuru değişkeni.|  
|`New`|`Using` Deyimin kaynağı alması durumunda gereklidir. Kaynağı zaten aldıysanız, ikinci söz dizimi alternatifini kullanın.|  
|`resourcetype`|Gerekli. Kaynağın sınıfı. Sınıfın <xref:System.IDisposable> arabirimini uygulaması gerekir.|  
|`arglist`|İsteğe bağlı. Bir örneği `resourcetype`oluşturmak için oluşturucuya geçirdiğiniz bağımsız değişkenlerin listesi. Bkz. [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`resourceexpression`|Gerekli. Gereksinimlerini karşılayan `resourcetype`bir sistem kaynağına başvuran değişken veya ifade. İkinci sözdizimi alternatif kullanırsanız, denetimi `Using` deyime geçirmeden önce kaynağı edinmeniz gerekir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bazen kodunuzun dosya tanıtıcısı, COM sarmalayıcısı veya SQL bağlantısı gibi yönetilmeyen bir kaynak olması gerekir. Bir `Using` blok, kodunuz ile işiniz bittiğinde bir veya daha fazla kaynağı elden çıkarma garantisi verir. Bu, diğer kodun kullanması için kullanılabilir hale getirir.  
  
 Yönetilen kaynaklar, .NET Framework atık toplayıcı (GC) tarafından, sizin bölümlemeden herhangi bir ek kodlama yapılmadan elden alınır. Yönetilen kaynaklar için bir `Using` bloğa ihtiyacınız yoktur. Ancak, çöp toplayıcıyı beklemek yerine `Using` , yönetilen bir kaynağın elden çıkarılmasını zorlamak için bir bloğu kullanmaya devam edebilirsiniz.  
  
 Bir `Using` blok üç bölümden oluşur: alım, kullanım ve çıkarma.  
  
- *Alım* , bir değişken oluşturma ve sistem kaynağına başvuracak şekilde başlatma anlamına gelir. Deyimde bir veya daha fazla kaynak alabilir ya da bloğu girmeden önce tam olarak bir kaynak alabilir ve bunu `Using` deyime sağlayabilirsiniz. `Using` Sağlarsanız `resourceexpression`, denetimi `Using` deyime geçirmeden önce kaynağı edinmeniz gerekir.  
  
- *Kullanım* , kaynaklara erişmek ve bunlarla eylemler gerçekleştirmek anlamına gelir. `Using` Ve`End Using` arasındaki deyimler, kaynakların kullanımını temsil eder.  
  
- *Aktiften çıkarma* , <xref:System.IDisposable.Dispose%2A> içindeki `resourcename`nesnesinde yöntemi çağırma anlamına gelir. Bu, nesnenin kaynaklarını düzgün bir şekilde sonlanmasına olanak tanır. Bildiri, `Using` blok denetimindeki kaynakları ortadan kaldırır. `End Using`  
  
## <a name="behavior"></a>Davranış  
 Bir blok bir `Try`... gibi davranır. `Using` bloğun kaynakları ve `Finally` blok kaldırmalarını kullandığı yapı. `Finally` `Try` Bu nedenle, bloğundan çıktığınızda `Using` bağımsız olarak blok kaynakların elden çıkarılmasını güvence altına alır. Bunun dışında <xref:System.StackOverflowException>, işlenmemiş bir özel durum durumunda da geçerlidir.  
  
 `Using` İfadesiyle alınan her kaynak değişkeninin kapsamı `Using` bloğuyla sınırlıdır.  
  
 `Using` Deyimde birden fazla sistem kaynağı belirtirseniz, efekt, bir diğeri içinde iç içe `Using` taşlarla aynı olur.  
  
 İse, hiçbir çağrı<xref:System.IDisposable.Dispose%2A> yapılmaz ve hiçbir özel durum oluşturulmaz. `Nothing` `resourcename`  
  
## <a name="structured-exception-handling-within-a-using-block"></a>Bir using bloğu Içinde yapılandırılmış özel durum Işleme  
 `Using` Blok içinde oluşabilecek bir özel durumu işlemeniz gerekiyorsa, bir bütün `Try`olarak bir işlem ekleyebilirsiniz... `Finally` oluşturma. `Using` Deyimin bir kaynağı alırken başarılı olmadığı durumu işlemeniz gerekiyorsa, olup olmadığını `resourcename` görmek `Nothing`için test edebilirsiniz.  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>Bir using bloğu yerine yapılandırılmış özel durum Işleme  
 Kaynakların alımı üzerinde daha fazla denetime ihtiyacınız varsa veya `Finally` blokta ek kod gerekiyorsa, `Using` engellemeyi bir `Try`... olarak yeniden yazabilirsiniz. `Finally` oluşturma. Aşağıdaki örnek, alma ve aktiften çıkarma `Try` `resource`ile `Using` eşdeğer olan iskelet ve kurulumlarını gösterir.  
  
```vb  
Using resource As New resourceType   
    ' Insert code to work with resource.  
End Using  
  
' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.  
Dim resource As New resourceType  
Try   
    ' Insert code to work with resource.  
Finally   
    If resource IsNot Nothing Then  
        resource.Dispose()   
    End If  
End Try   
```  
  
> [!NOTE]
> `Using` Bloğun içindeki kod `resourcename` nesneyi başka bir değişkene atamamalıdır. `Using` Bloğundan çıktığınızda, kaynak atılmış olur ve diğer değişken işaret ettiği kaynağa erişemez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, log. txt adlı bir dosya oluşturur ve dosyaya iki satırlık metin yazar. Örnek ayrıca aynı dosyayı okur ve metin satırlarını görüntüler.  
  
 Ve sınıfları arabirimini uygulamadığından, kod, yazma ve okuma işlemlerinden sonra `Using` dosyanın doğru şekilde kapatılmasını sağlamak için deyimlerini kullanabilir. <xref:System.IDisposable> <xref:System.IO.TextReader> <xref:System.IO.TextWriter>  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable>
- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Nasıl yapılır: Sistem kaynağını atma](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
