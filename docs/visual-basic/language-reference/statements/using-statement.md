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
ms.openlocfilehash: 819af63acb6a1f038300bcb999dcfb904eb8a457
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592085"
---
# <a name="using-statement-visual-basic"></a>Using Deyimi (Visual Basic)

@No__t-0 bloğunun başlangıcını bildirir ve isteğe bağlı olarak blok denetimlerinin bulunduğu sistem kaynaklarını alır.

## <a name="syntax"></a>Sözdizimi

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a>Bölümler

|Terim|Tanım|  
|---|---|  
|`resourcelist`|@No__t (0) belirtmezseniz gereklidir. Bu `Using` blok denetimlerinin denetimlerin virgülle ayrıldığı bir veya daha fazla sistem kaynağı listesi.|  
|`resourceexpression`|@No__t (0) belirtmezseniz gereklidir. Bu `Using` bloğu tarafından denetlenerek bir sistem kaynağını işaret eden başvuru değişkeni veya ifadesi.|  
|`statements`|İsteğe bağlı. @No__t-0 bloğunun çalıştığı deyimler bloğu.|  
|`End Using`|Gerekli. @No__t-0 bloğunun tanımını ve denetlediği tüm kaynakların bir kısmını sonlandırır.|  

 @No__t-0 parçasındaki her kaynak aşağıdaki söz dizimi ve bölümlere sahiptir:

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 veya

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a>resourceList bölümleri

|Terim|Tanım|  
|---|---|  
|`resourcename`|Gerekli. @No__t-0 bloğunun denetlediği bir sistem kaynağına başvuran başvuru değişkeni.|  
|`New`|@No__t-0 ifadesinde kaynak elde ederseniz gereklidir. Kaynağı zaten aldıysanız, ikinci söz dizimi alternatifini kullanın.|  
|`resourcetype`|Gerekli. Kaynağın sınıfı. Sınıfın <xref:System.IDisposable> arabirimini uygulaması gerekir.|  
|`arglist`|İsteğe bağlı. @No__t-0 örneğini oluşturmak için oluşturucuya geçirdiğiniz bağımsız değişkenlerin listesi. Bkz. [parametre listesi](parameter-list.md).|  
|`resourceexpression`|Gerekli. @No__t-0 gereksinimlerini karşılayan bir sistem kaynağına başvuran değişken veya ifade. İkinci sözdizimi alternatif kullanırsanız, denetimi `Using` ifadesine geçirmeden önce kaynağı edinmeniz gerekir.|  
  
## <a name="remarks"></a>Açıklamalar

 Bazen kodunuzun dosya tanıtıcısı, COM sarmalayıcısı veya SQL bağlantısı gibi yönetilmeyen bir kaynak olması gerekir. @No__t-0 bloğu, kodunuz ile işiniz bittiğinde bir veya daha fazla kaynağı elden çıkarma garantisi verir. Bu, diğer kodun kullanması için kullanılabilir hale getirir.

 Yönetilen kaynaklar, .NET Framework atık toplayıcı (GC) tarafından, sizin bölümlemeden herhangi bir ek kodlama yapılmadan elden alınır. Yönetilen kaynaklar için `Using` bloğuna ihtiyacınız yoktur. Ancak, atık toplayıcıyı beklemek yerine, yönetilen bir kaynağın elden çıkarılmasını zorlamak için `Using` bloğu kullanmaya devam edebilirsiniz.

 @No__t-0 bloğu üç bölümden oluşur: alma, kullanım ve çıkarma.

- *Alım* , bir değişken oluşturma ve sistem kaynağına başvuracak şekilde başlatma anlamına gelir. @No__t-0 ifadesinde bir veya daha fazla kaynak alabilir ya da bloğu girmeden önce tam olarak bir kaynak alabilir ve bunu `Using` ifadesine sağlayamazsınız. @No__t-0 sağlarsanız, denetimi `Using` ifadesine geçirmeden önce kaynağı edinmeniz gerekir.

- *Kullanım* , kaynaklara erişmek ve bunlarla eylemler gerçekleştirmek anlamına gelir. @No__t-0 ve `End Using` arasındaki deyimler, kaynakların kullanımını temsil eder.

- *Aktiften çıkarma* , <xref:System.IDisposable.Dispose%2A> yönteminin `resourcename` içindeki nesne üzerinde çağrılması anlamına gelir. Bu, nesnenin kaynaklarını düzgün bir şekilde sonlanmasına olanak tanır. @No__t-0 deyimleri, `Using` bloğunun denetimindeki kaynakları ortadan kaldırır.

## <a name="behavior"></a>Davranış

 @No__t-0 bloğu, `Try` bloğunun kaynakları ve @no__t 4 blok tarafından kullanıldığı `Try`... `Finally` oluşturma gibi davranır. Bu nedenle, `Using` bloğu, bloğundan çıktığınızda bağımsız olarak kaynakları elden çıkarma garantisi verir. Bu, <xref:System.StackOverflowException> dışında işlenmeyen bir özel durum durumunda bile geçerlidir.

 @No__t-0 ifadesiyle alınan her kaynak değişkeninin kapsamı `Using` bloğu ile sınırlıdır.

 @No__t-0 ifadesinde birden fazla sistem kaynağı belirtirseniz, efekt, `Using` blokları diğeri içinde iç içe yerleştirilmiş şekilde aynı olur.

 @No__t-0 `Nothing` ise, <xref:System.IDisposable.Dispose%2A> çağrısı yapılmaz ve hiçbir özel durum oluşturulmaz.

## <a name="structured-exception-handling-within-a-using-block"></a>Bir using bloğu Içinde yapılandırılmış özel durum Işleme

 @No__t-0 bloğunda oluşabilecek bir özel durumu işlemeniz gerekiyorsa, buna tam bir `Try`... `Finally` yapımı ekleyebilirsiniz. @No__t-0 ifadesinin bir kaynağı alırken başarılı olmadığı durumu işlemeniz gerekiyorsa, `resourcename` ' in `Nothing` olup olmadığını görmek için test edebilirsiniz.

## <a name="structured-exception-handling-instead-of-a-using-block"></a>Bir using bloğu yerine yapılandırılmış özel durum Işleme

 Kaynakların alımı üzerinde daha hassas denetime ihtiyacınız varsa veya `Finally` bloğunda ek koda ihtiyacınız varsa, `Using` bloğunu `Try`... `Finally` oluşturma olarak yeniden yazabilirsiniz. Aşağıdaki örnekte, `resource` ' nin alımı ve aktiften çıkarılması ile eşdeğer olan iskelet `Try` ve `Using` kurulumlarını gösterilmektedir.

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
> @No__t-0 bloğunun içindeki kod, `resourcename` ' deki nesneyi başka bir değişkene atamamalıdır. @No__t-0 bloğundan çıktığınızda, kaynak atılmış olur ve diğer değişken işaret ettiği kaynağa erişemez.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, log. txt adlı bir dosya oluşturur ve dosyaya iki satırlık metin yazar. Örnek ayrıca aynı dosyayı okur ve metin satırlarını görüntüler:

 @No__t-0 ve <xref:System.IO.TextReader> sınıfları <xref:System.IDisposable> arabirimini uygulamadığından, kod, yazma ve okuma işlemlerinden sonra dosyanın doğru şekilde kapatılmasını sağlamak için `Using` deyimlerini kullanabilir.

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable>
- [Try...Catch...Finally Deyimi](try-catch-finally-statement.md)
- [Nasıl yapılır: Bir sistem kaynağını atma @ no__t-0
