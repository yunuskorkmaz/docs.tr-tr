---
title: Çalışma Zamanı Aranabilir Sarmalayıcısı
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, COM wrappers
- RCW
- COM wrappers
- runtime callable wrappers
- interoperation with unmanaged code, COM wrappers
ms.assetid: 7e542583-1e31-4e10-b523-8cf2f29cb4a4
ms.openlocfilehash: 0b448379fba965060fdf3bf067e65374f40d1fc2
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156016"
---
# <a name="runtime-callable-wrapper"></a>Çalışma Zamanı Aranabilir Sarmalayıcısı
Ortak dil çalışma zamanı, COM nesnelerini, çalışma zamanı çağrılabilir sarmalayıcı (RCW) adlı bir ara sunucu üzerinden kullanıma sunar. RCW, .NET istemcilerine sıradan bir nesne gibi görünse de, birincil işlevi bir .NET istemcisiyle COM nesnesi arasındaki çağrıları sıralayamaz.  
  
 Çalışma zamanı, bu nesnede bulunan başvuruların sayısından bağımsız olarak her bir COM nesnesi için tam olarak bir RCW oluşturur. Çalışma zamanı her bir nesne için işlem başına tek bir RCW tutar.  Bir uygulama etki alanında veya grupta bir RCW oluşturup daha sonra başka bir uygulama etki alanına veya gruba bir başvuru geçirirseniz, ilk nesneye yönelik bir ara sunucu kullanılacaktır.  Aşağıdaki çizimde gösterildiği gibi, herhangi bir sayıda yönetilen istemci, INEW ve INewer arabirimlerini sunan COM nesnelerine bir başvuru tutabilir.  

Aşağıdaki görüntüde, çalışma zamanında çağrılabilir sarmalayıcı aracılığıyla COM nesnelerine erişme işlemi gösterilmektedir:

 ![RCW aracılığıyla COM nesnelerine erişme işlemi.](./media/runtime-callable-wrapper/runtime-callable-wrapper.gif)  

 Bir tür kitaplığından türetilmiş meta verileri kullanarak, çalışma zamanı hem çağrılan COM nesnesini hem de bu nesne için bir sarmalayıcı oluşturur. Her RCW, nesne sarmaladığı COM nesnesinde bir arabirim işaretçileri önbelleği tutar ve RCW artık gerekmiyorsa COM nesnesinde başvurusunu yayınlar. Çalışma zamanı RCW üzerinde çöp toplama işlemi gerçekleştirir.  
  
 Diğer etkinliklerin yanı sıra, RCW, Sarmalanan nesne adına yönetilen ve yönetilmeyen kod arasında veri sıraladığında. Özellikle, RCW, istemci ve sunucu aralarında geçen verilerin farklı temsillerine sahip olduğunda, yöntem bağımsız değişkenleri ve yöntem dönüş değerleri için sıralama sağlar.  
  
 Standart sarmalayıcı, yerleşik sıralama kurallarını uygular. Örneğin, bir .NET istemcisi bir dize türünü yönetilmeyen bir nesneye bir bağımsız değişkenin parçası olarak geçirdiğinde, sarmalayıcı dizeyi bir BSTR türüne dönüştürür. COM nesnesi, yönetilen çağıranına bir BSTR döndürmelidir, çağıran bir dize alır. Hem istemci hem de sunucu onlara tanıdık gelen verileri gönderir ve alır. Diğer türler dönüştürme gerektirmez. Örneğin, standart bir sarmalayıcı, türü dönüştürmeden yönetilen ve yönetilmeyen kod arasında her zaman 4 baytlık bir tamsayı geçilecektir.  
  
## <a name="marshaling-selected-interfaces"></a>Seçili arabirimler sıralanıyor  
 [Çalışma zamanı çağrılabilir sarmalayıcı](runtime-callable-wrapper.md) (RCW) birincil hedefi, yönetilen ve yönetilmeyen programlama modelleri arasındaki farkları gizmaktır. Sorunsuz bir geçiş oluşturmak için RCW, aşağıdaki çizimde gösterildiği gibi, seçili COM arabirimlerini .NET istemcisine göstermeden tüketir.

 Aşağıdaki görüntüde COM arabirimleri ve çalışma zamanı çağrılabilir sarmalayıcı gösterilmektedir:
  
 ![Arabirimleri olan çalışma zamanı çağrılabilir sarmalayıcının ekran görüntüsü.](./media/runtime-callable-wrapper/runtime-callable-wrapper-interfaces.gif)  
  
 Erken bağlantılı bir nesne olarak oluşturulduğunda RCW belirli bir türdür. COM nesnesinin uyguladığı arabirimleri uygular ve nesne arabirimlerinden yöntemleri, özellikleri ve olayları gösterir. Çizimde RCW, INEW arabirimini kullanıma sunar, ancak **IUnknown** ve **IDispatch** arabirimlerini kullanır. Ayrıca, RCW, .NET istemcisine INew arabiriminin tüm üyelerini kullanıma sunar.  
  
 RCW, sarmaladığı nesne tarafından açığa çıkarılan aşağıdaki tabloda listelenen arabirimleri kullanır.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|**IDispatch**|Yansıma aracılığıyla COM nesnelerine geç bağlama için.|  
|**IErrorInfo**|Hatanın metinsel bir açıklamasını, kaynağını, bir yardım dosyasını, yardım bağlamını ve hatayı tanımlayan arabirimin GUID 'sini (her zaman .NET sınıfları için **GUID_NULL** ) sağlar.|  
|**IProvideClassInfo**|Sarmalanan COM nesnesi **IProvideClassInfo**uyguluyorsa, RCW daha iyi tür kimliği sağlamak için bu arabirimden tür bilgilerini ayıklar.|  
|**IUnknown**|Nesne kimliği, tür zorlaması ve ömür yönetimi için:<br /><br /> -Nesne kimliği<br />     Çalışma zamanı, her nesne için **IUnknown** arabiriminin DEĞERINI karşılaştırarak com nesneleri arasında ayrım yapar.<br />-Tür zorlaması<br />     RCW, **QueryInterface** yöntemi tarafından gerçekleştirilen dinamik tür bulmayı tanır.<br />-Ömür yönetimi<br />     **QueryInterface** metodunu kullanarak, RCW, çalışma zamanı sarmalayıcı üzerinde çöp toplama işlemi gerçekleştirene kadar yönetilmeyen nesneye bir başvuru alır ve bu başvuruyu barındırır.|  
  
 RCW isteğe bağlı olarak, sarmaladığı nesne tarafından açığa çıkarılan aşağıdaki tabloda listelenen arabirimleri kullanır.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|**Inewctionpoint** ve **IConnectionPointContainer**|RCW, bağlantı noktası olay stilini kullanıma sunan nesneleri temsilci tabanlı olaylara dönüştürür.|  
|**IDispatchEx** (yalnızca .NET Framework) |Sınıf **IDispatchEx**uygularsa, RCW, **Ida**uygular. **IDispatchEx** **arabirimi IDispatch arabiriminin bir** uzantısıdır. Bu, **IDispatch**'in aksine numaralandırma, ekleme, silme ve büyük/küçük harf duyarlı üyelerin çağrılmasını mümkün değildir.|  
|**IEnumVariant**|Numaralandırmalar destekleyen COM türlerinin koleksiyonlar olarak değerlendirilmesini sağlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM sarmalayıcıları](com-wrappers.md)
- [COM Aranabilir Sarmalayıcısı](com-callable-wrapper.md)
- [Tür kitaplığını derlemeye dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tür Kitaplığını Derleme Olarak İçeri Aktarma](../../framework/interop/importing-a-type-library-as-an-assembly.md)
