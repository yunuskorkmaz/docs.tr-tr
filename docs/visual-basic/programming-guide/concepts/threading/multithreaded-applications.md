---
title: Birden çok iş parçacıklı uygulamalar (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 02b0444b-2e68-4f2c-bc28-28c046004017
ms.openlocfilehash: ab4b8d1c77ae75aee6f2cf459258766f88d86abe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650484"
---
# <a name="multithreaded-applications-visual-basic"></a>Birden çok iş parçacıklı uygulamalar (Visual Basic)
Visual Basic ile aynı anda birden çok görevleri uygulamaları yazabilirsiniz. Diğer görevleri bulunduran olası görevlerle olarak da bilinen bir işlem ayrı iş parçacıklarına, yürütebilir *çoklu iş parçacığı kullanımı* veya *iş parçacığı oluşturma serbest*.  
  
 Çoklu iş parçacığı kullanımı yoğun işlemci kullanır görevlerinin gibi kullanıcı arabirimi etkin kalmasını çünkü kullanıcı girişi için daha iyi yanıt uygulamaları iş parçacıklarını ayırın. Ölçeklenebilir uygulamalar oluşturduğunuzda, iş yükü arttıkça iş parçacığı ekleyebilirsiniz olduğundan çoklu iş parçacığı kullanımı de yararlıdır.  
  
## <a name="creating-and-using-threads"></a>Oluşturma ve iş parçacığı kullanma  
 Uygulamanızın iş parçacığı davranışı hakkında daha fazla denetime ihtiyacınız varsa, iş parçacıklarının kendiniz yönetebilirsiniz. Ancak, doğru birden çok iş parçacıklı uygulamalar yazma zor olabileceğini unutmayın: uygulamanızı yanıt vermemesine veya yarış durumları tarafından kaynaklanan geçici hataları deneyimi. Daha fazla bilgi için bkz: [iş parçacığı bileşenlerini](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).  
  
 Türünde bir değişken bildirerek yeni bir iş parçacığı oluşturma <xref:System.Threading.Thread> ve sağlayan yordam veya yeni iş parçacığını yürütmek istediğiniz yöntemi adı Oluşturucusu çağırma. Aşağıdaki kod bir örnek sağlar.  
  
```vb  
Dim newThread As New System.Threading.Thread(AddressOf AMethod)  
```  
  
### <a name="starting-and-stopping-threads"></a>Başlangıç ve iş parçacıklarını durdurma  
 Yeni bir iş parçacığı yürütülmesi başlatmak için kullanmak <xref:System.Threading.Thread.Start%2A> aşağıdaki kodda gösterildiği gibi yöntemi.  
  
```vb  
newThread.Start()  
```  
  
 Bir iş parçacığı yürütülmesini durdurmak için kullanma <xref:System.Threading.Thread.Abort%2A> aşağıdaki kodda gösterildiği gibi yöntemi.  
  
```vb  
newThread.Abort()  
```  
  
 Başlangıç ve iş parçacıklarını durdurma yanı sıra, ayrıca iş parçacığı çağırarak duraklatabilirsiniz <xref:System.Threading.Thread.Sleep%2A> veya <xref:System.Threading.Thread.Suspend%2A> yöntemi, askıya alınmış bir iş parçacığını kullanarak devam <xref:System.Threading.Thread.Resume%2A> yöntemini kullanarak bir iş parçacığı yok edin <xref:System.Threading.Thread.Abort%2A> yöntemi  
  
### <a name="thread-methods"></a>İş parçacığı yöntemleri  
 Aşağıdaki tabloda, tek tek iş parçacıklarını denetlemek için kullanabileceğiniz yöntemlerden bazıları gösterilmektedir.  
  
|Yöntem|Eylem|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A>|Çalışmaya başlamak bir iş parçacığı neden olur.|  
|<xref:System.Threading.Thread.Sleep%2A>|Bir iş parçacığı belirli bir süre boyunca duraklatır.|  
|<xref:System.Threading.Thread.Suspend%2A>|Bir iş parçacığı güvenli bir noktasına ulaştığında duraklatır.|  
|<xref:System.Threading.Thread.Abort%2A>|Bir iş parçacığı güvenli bir noktasına ulaştığında durdurur.|  
|<xref:System.Threading.Thread.Resume%2A>|Askıya alınmış bir iş parçacığı yeniden başlatır|  
|<xref:System.Threading.Thread.Join%2A>|Bitirmek başka bir iş parçacığı için beklenecek geçerli iş parçacığının neden olur. Bir zaman aşımı değeri ile kullandıysanız, bu yöntem `True` iş parçacığı ayrılan zaman içinde tamamlanırsa.|  
  
### <a name="safe-points"></a>Güvenli noktalar  
 Bu yöntemlerin çoğu kendinden açıklamalıdır, ancak kavramı *güvenli noktalar* için yeni olabilir. Güvenli noktalarıdır kod olduğu ortak dil çalışma zamanı için güvenli otomatik gerçekleştirmek için konumlarda *çöp toplama*, kullanılmayan değişkenleri serbest bırakma ve bellek geri kazanma işlemini. Çağırdığınızda <xref:System.Threading.Thread.Abort%2A> veya <xref:System.Threading.Thread.Suspend%2A> bir iş parçacığı, ortak dil çalışma zamanı yöntemi kodunu analiz eder ve çalışan durdurmak iş parçacığı için uygun bir konumda konumunu belirler.  
  
### <a name="thread-properties"></a>İş parçacığı özellikleri  
 İş parçacığı, ayrıca aşağıdaki tabloda gösterildiği gibi çeşitli yararlı özellikleri içerir:  
  
|Özellik|Değer|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Değeri içeren `True` bir iş parçacığı etkin olması durumunda.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Alır veya bir iş parçacığı olduğundan veya bir arka plan iş parçacığı olmalıdır olmadığını belirten bir Boole değeri ayarlar. Arka plan iş parçacıkları gibi ön plan iş parçacıkları olsa da bir arka plan iş parçacığı durdurma gelen bir işlem engellemez. Bir işleme ait tüm ön plan iş parçacıkları durdurulduğunda ortak dil çalışma zamanı işlem çağırarak sona <xref:System.Threading.Thread.Abort%2A> hala etkin arka plan iş parçacıkları yöntemi.|  
|<xref:System.Threading.Thread.Name%2A>|Alır veya bir iş parçacığı adını ayarlar. Hata ayıklama tek tek iş parçacığı bulmak için en sık kullanılır.|  
|<xref:System.Threading.Thread.Priority%2A>|Alır veya iş parçacığı planlama önceliğini belirlemek için işletim sistemi tarafından kullanılan bir değer ayarlar.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Bir iş parçacığının durumu veya durumları tanımlayan bir değer içeriyor.|  
  
## <a name="thread-priorities"></a>İş parçacığı öncelikler  
 Her iş parçacığı nasıl büyük veya küçük bir dilim yürütmek için sahip işlemci zamanını belirleyen bir öncelik özelliğine sahiptir. İşletim sistemi, yüksek öncelikli iş parçacıklarını uzun zaman dilimi ve düşük öncelikli parçacıkları daha kısa bir zaman dilimi ayırır. Yeni iş parçacıkları değeri ile oluşturulan `Normal`, ancak bunu değiştirebilirsiniz <xref:System.Threading.Thread.Priority%2A> herhangi bir değer özelliğine <xref:System.Threading.ThreadPriority> numaralandırması.  
  
 Bkz: <xref:System.Threading.ThreadPriority> çeşitli iş parçacığı öncelikleri ayrıntılı bir açıklaması.  
  
## <a name="foreground-and-background-threads"></a>Ön Plan ve Arka Plan İş Parçacıklarını Seçme  
 A *ön plan iş parçacığı* süresiz olarak, ancak çalışan bir *arka plan iş parçacığı* son ön plan iş parçacığı durduruldu hemen durdurur. Kullanabileceğiniz <xref:System.Threading.Thread.IsBackground%2A> belirlemek ya da bir iş parçacığı arka plan durumunu değiştirmek için özellik.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Thread>  
 [İş parçacığı eşitleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [Parametreler ve dönüş değerleri birden çok iş parçacıklı yordamlar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)  
 [İş parçacığı oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)
