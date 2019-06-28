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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cc4b691763c1aff4bacc2935a0a6cf32c880180
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422610"
---
# <a name="runtime-callable-wrapper"></a>Çalışma Zamanı Aranabilir Sarmalayıcısı
Ortak dil çalışma zamanı, COM nesneleri çalışma zamanı çağrılabilir sarmalayıcı (RCW) adlı bir ara sunucu aracılığıyla kullanıma sunar. RCW, .NET istemcileri için normal bir nesne görünmesine karşın, birincil bir .NET istemcisi ve COM nesnesi arasındaki çağrıların sıralamakta işlevidir.  
  
 Çalışma zamanı, nesne üzerinde mevcut başvuruları sayısından bağımsız olarak her bir COM nesnesi için tam olarak bir RCW oluşturur. Çalışma zamanı, her nesne için işlem başına tek bir RCW tutar.  Bir uygulama etki alanı veya grup bir RCW oluşturun ve ardından başka bir uygulama etki alanı ya da grup bir başvuru geçirin, ilk nesneye bir ara sunucu kullanılır.  Aşağıdaki çizimde gösterildiği gibi yönetilen istemcilerin herhangi bir sayıda INew ve INewer arabirimler sunun COM nesnelerine başvuru barındırabilir.  

Aşağıdaki görüntüde, çalışma zamanı çağrılabilir sarmalayıcı COM nesnelerine erişme işlemi gösterilmektedir:

 ![COM nesneleri RCW erişme işlemi.](./media/runtime-callable-wrapper/runtime-callable-wrapper.gif)  

 Türetilmiş bir tür kitaplığından meta verileri kullanarak, çalışma zamanı hem çağrılan COM nesnesi hem de bu nesne için bir sarmalayıcı oluşturur. Her RCW arabirim işaretçilerini sarmalar ve RCW artık gerekli olmadığında, başvuru COM nesnesi üzerinde serbest COM nesne üzerinde bir önbelleğini korur. Çalışma zamanı üzerinde RCW atık toplama gerçekleştirir.  
  
 Diğer etkinlikler arasında RCW Sarmalanan nesne adına yönetilen ve yönetilmeyen kod arasında veri sürekliliğe devreder. Özellikle, RCW, istemci ve sunucu, aralarında aktarılan verilerin farklı temsilleri olabilir her yöntem bağımsız değişkenleri ve yöntem dönüş değerleri için sıralama sağlar.  
  
 Standart sarmalayıcı yerleşik sıralama kuralları zorlar. Örneğin, bir .NET istemci yönetilmeyen bir nesneye bağımsız değişken bir parçası olarak bir dize türü geçtiğinde sarmalayıcı dize bir BSTR türüne dönüştürür. COM nesnesinin yönetilen arayanına BSTR döndürmelidir, çağıran bir dize alır. İstemci ve sunucu gönderin ve onlara alışkın olduğu veri alın. Diğer türleri dönüştürme gerektirir. Örneğin, standart bir sarmalayıcı türü dönüştürme olmadan yönetilen ve yönetilmeyen kod arasındaki her zaman bir 4 baytlık tamsayı geçer.  
  
## <a name="marshaling-selected-interfaces"></a>Seçilen arabirimleri sıralama  
 Birincil amacı [çalışma zamanı çağrılabilir sarmalayıcı](runtime-callable-wrapper.md) (RCW) yönetilen ve yönetilmeyen programlama modelleri arasındaki farkları Gizle etmektir. Sorunsuz bir geçiş oluşturmak için RCW Seçili COM arabirimleri .NET istemciye sokmadan aşağıdaki çizimde gösterildiği gibi kullanır. 

 Aşağıdaki görüntüde, COM arabirimlerinde ve çalışma zamanı çağrılabilir sarmalayıcı gösterilmektedir: 
  
 ![Çalışma zamanı çağrılabilir sarmalayıcı arabirimleri ile ekran görüntüsü.](./media/runtime-callable-wrapper/runtime-callable-wrapper-interfaces.gif)  
  
 RCW bir erken bağlanan nesne olarak oluşturduğunuzda, belirli bir türdür. Bu, COM nesnesi uygular ve yöntemler, özellikler ve olaylar nesnenin arabirimlerinden sunan arabirimlerini uygular. Çizimde, RCW INew arabirimini kullanıma sunar ancak tüketir **IUnknown** ve **IDispatch** arabirimleri. Ayrıca, RCW, .NET istemci INew arabirimin tüm üyeleri ortaya koyar.  
  
 Aşağıdaki tabloda listelenen arabirimler sarmaladığı nesne tarafından sunulan RCW tüketir.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|**IDispatch**|COM nesnelerine üzerinden erişiyorsanız geç bağlama için.|  
|**IErrorInfo**|Hata, kaynağı, bir Yardım dosyası, Yardım bağlamı ve hata tanımlı arabiriminin GUID'si değerinin metinsel bir açıklaması verilmiştir (her zaman **GUID_NULL** .NET sınıfları için).|  
|**IProvideClassInfo**|COM Nesne uygulayan sarılan, **Iprovideclassınfo**, RCW, daha iyi tür kimlik sağlamak için bu arabirimden tür bilgilerini ayıklar.|  
|**IUnknown**|Nesne kimliği, türü zorlama ve ömür yönetimi için:<br /><br /> -Nesne Kimliği<br />     Çalışma zamanı değerini karşılaştırarak COM nesneleri ayırt **IUnknown** her nesne için arabirim.<br />-Type zorlama<br />     Dinamik tür bulma tarafından gerçekleştirilen RCW tanır **QueryInterface** yöntemi.<br />-Ömür Yönetimi<br />     Kullanarak **QueryInterface** yöntemi, RCW alır ve çalışma zamanının çöp toplama, yönetilmeyen nesneyi serbest sarmalayıcı başarılı olana dek, yönetilmeyen bir nesneye bir başvuru içerir.|  
  
 RCW, aşağıdaki tabloda listelenen arabirimler sarmaladığı nesne tarafından sunulan isteğe bağlı olarak kullanır.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|**IConnectionPoint** ve **IConnectionPointContainer**|Bağlantı noktası olayı stili için temsilci tabanlı olay kullanıma RCW dönüştürür nesneleri.|  
|**Idispatchex**|Sınıf uyguluyorsa **Idispatchex**, RCW uygulayan **IExpando**. **Idispatchex** arabirimi uzantısıdır **IDispatch** aksine, arabirim **IDispatch**, numaralandırma, ekleme, silme, sağlar ve büyük/küçük harfe üyeleri çağırma.|  
|**IEnumVARIANT**|Koleksiyon olarak kabul edilmesi için numaralandırmalar destekleyen COM türleri sağlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM Sarmalayıcıları](com-wrappers.md)
- [COM Çağrılabilir Sarmalayıcısı](com-callable-wrapper.md)
- [Tür kitaplığını derlemeye dönüştürme özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
