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
ms.openlocfilehash: fe53ea58dc98a4de793fe9dad1c3ceeac71622fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843207"
---
# <a name="using-statement-visual-basic"></a>Using Deyimi (Visual Basic)
Başlangıcı bildiren bir `Using` engelleyin ve isteğe bağlı olarak blok denetleyen sistem kaynaklarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`resourcelist`|Gerekli değil sağladığınız varsa `resourceexpression`. Listesinde bir veya daha fazla sistem kaynakları bu `Using` block denetimleri, virgülle ayrılmış.|  
|`resourceexpression`|Gerekli değil sağladığınız varsa `resourcelist`. Başvuru değişkenin veya ifadenin bu tarafından denetlenmesi için bir sistem kaynağını başvuran `Using` blok.|  
|`statements`|İsteğe bağlı. Deyimler bloğunu, `Using` bloğu çalışır.|  
|`End Using`|Gerekli. Tanımını sonlandırır `Using` bloğu hem de denetlediğini tüm kaynakları siler.|  
  
 Her kaynağın `resourcelist` bölümü aşağıdaki söz dizimini ve bölümleri sahiptir:  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 veya  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourcelist bölümleri  
  
|Terim|Tanım|  
|---|---|  
|`resourcename`|Gerekli. Bir sistem kaynağa başvuruda bulunan bir başvuru değişkenini, `Using` denetimleri engelleyin.|  
|`New`|Gerekli if `Using` deyimi kaynak alır. Kaynak aldıysanız, ikinci sözdizimi alternatifi kullanın.|  
|`resourcetype`|Gerekli. Kaynak sınıfı. Sınıf uygulamalıdır <xref:System.IDisposable> arabirimi.|  
|`arglist`|İsteğe bağlı. Oluşturucuya bir örneğini oluşturmak için kaçı bağımsız değişkenlerinin listesi `resourcetype`. Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`resourceexpression`|Gerekli. Değişkenin veya ifadenin gereksinimlerini karşılayan bir sistem kaynağa başvuran `resourcetype`. İkinci sözdizimi alternatif kullanırsanız, kaynak denetimine geçirmeden önce almalıdır `Using` deyimi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bazen bir dosya tanıtıcısı, COM sarmalayıcı veya bir SQL bağlantı gibi yönetilmeyen bir kaynağı kodunuzu gerektirir. A `Using` blok kodunuz ile bunları tamamlandığında bir veya daha fazla gibi kaynakların elden garanti eder. Bu bunları kullanmak başka bir kod için kullanılabilir yapar.  
  
 Yönetilen kaynaklar, .NET Framework atık toplayıcı (GC) tarafından ek kodlamaya bulunmanıza gerek kalmadan kaldırıldıklarından. Gereksinim duymadığınız bir `Using` yönetilen kaynaklar için blok. Ancak, yine de kullanabileceğiniz bir `Using` çöp toplayıcının beklemek yerine bir yönetilen kaynak elden zorlamak için blok.  
  
 A `Using` bloğu üç bölümü vardır: alım, kullanım ve silinecek.  
  
-   *Alım* bir değişken oluşturma ve sistem kaynağına başvurmak için başlatma anlamına gelir. `Using` Deyimi bir veya daha fazla kaynak elde veya tam olarak bir kaynak blok girmeden önce almak ve sağlamak için `Using` deyimi. Sağlarsanız, `resourceexpression`, kaynak denetimine geçirmeden önce almalıdır `Using` deyimi.  
  
-   *Kullanım* kaynaklara erişirken ve bunları eylemleri gerçekleştirme anlamına gelir. Deyimleri arasında `Using` ve `End Using` kaynak kullanımını gösterir.  
  
-   *Çıkarma* çağırma anlamına gelir <xref:System.IDisposable.Dispose%2A> nesneye yöntemi `resourcename`. Bu nesne kaynaklarını düzgün bir şekilde sonlandırmak sağlar. `End Using` Deyimi siler altında kaynakların `Using` bloğun denetimi.  
  
## <a name="behavior"></a>Davranış  
 A `Using` blok davranacağını gibi bir `Try`... `Finally` , yapım `Try` blok kaynakları kullanır ve `Finally` blok onları siler. Bu nedenle, `Using` blok blok çıkış ne olursa olsun, kaynakların elden garanti eder. Hatta işlenmeyen bir özel durum söz konusu olduğunda, bu doğrudur dışında bir <xref:System.StackOverflowException>.  
  
 Tarafından alınan her kaynak değişkenin kapsamını `Using` deyimdir sınırlı `Using` blok.  
  
 Birden fazla sistem kaynağında belirtirseniz `Using` deyimi, etkin olduğu aynı iç içe kabul `Using` içindeki başka bir engeller.  
  
 Varsa `resourcename` olduğu `Nothing`, hiçbir <xref:System.IDisposable.Dispose%2A> yapılmış ve hiçbir özel durum.  
  
## <a name="structured-exception-handling-within-a-using-block"></a>Yapılandırılmış özel durum işleme kullanan bir blok içinde  
 İçinde oluşabilecek bir özel durumu işlemek gereken `Using` bloğu tam ekleyebilirsiniz `Try`... `Finally` ona oluşturma. Durumu işlemek gerekirse burada `Using` deyimi, bir kaynak edinilirken başarılı değil, olmadığını sınayabilirsiniz `resourcename` olduğu `Nothing`.  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>Yapılandırılmış özel durum işleme kullanan bir bloğu yerine  
 Edinme kaynakları üzerinde daha hassas bir denetime ihtiyacınız varsa veya ek kod, ihtiyaç duyarsanız `Finally` bloğu, yeniden `Using` olarak engelleyecek bir `Try`... `Finally` oluşturma. Aşağıdaki örnek, çatı gösterir `Try` ve `Using` edinme ve elden yapılarını `resource`.  
  
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
>  İçinde kod `Using` blok atama nesnesinde `resourcename` başka bir değişkene. Çıktığınızda `Using` blok, kaynak bırakıldı ve diğer değişkenin işaret ettiği kaynağa erişemiyor.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki satırlık bir metin dosyasına yazar ve log.txt adlı bir dosya oluşturur. Örnek ayrıca, aynı dosyasını okur ve metin satırlarını görüntüler.  
  
 Çünkü <xref:System.IO.TextWriter> ve <xref:System.IO.TextReader> sınıfları uygulama <xref:System.IDisposable> arabirimi, kod kullanabileceğiniz `Using` deyimlerini dosyanın doğru kapalı sonra yazma ve okuma işlemleri sağlamak için.  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable>
- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Nasıl yapılır: Bir sistem kaynağını atma](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
