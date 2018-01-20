---
title: "Çalışma Zamanı Aranabilir Sarmalayıcısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, COM wrappers
- RCW
- COM wrappers
- runtime callable wrappers
- interoperation with unmanaged code, COM wrappers
ms.assetid: 7e542583-1e31-4e10-b523-8cf2f29cb4a4
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8fed5ff57a4674f9b7723b1b850e972316fa94fb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="runtime-callable-wrapper"></a>Çalışma Zamanı Aranabilir Sarmalayıcısı
Ortak dil çalışma zamanı çalışma zamanı aranabilir sarmalayıcısı (RCW) adlı bir proxy üzerinden COM nesneleri gösterir. RCW .NET istemcileri sıradan bir nesneye görünmesine karşın, bir .NET istemcisi ve COM nesnesi arasındaki aramaları sıralamakta kendi birincil işlevi olduğu.  
  
 Çalışma zamanı bu nesne üzerinde mevcut başvuruları sayısından bağımsız olarak her COM nesnesi için tam olarak bir RCW oluşturur. Çalışma zamanı her nesne için işlem başına tek bir RCW tutar.  Bir uygulama etki alanı veya grup bir RCW oluşturun ve daha sonra başka bir uygulama etki alanı ya da Grup başvuru geçirin, ilk nesne için bir proxy kullanılır.  Aşağıdaki çizimde gösterildiği gibi herhangi bir sayıda yönetilen istemciler INew ve INewer arabirimleri kullanıma COM nesnelerine başvuru basılı tutabilirsiniz.  
  
 ![RCW](../../../docs/framework/interop/media/rcw.gif "rcw")  
Çalışma zamanı aranabilir sarmalayıcısı COM nesnelerine erişme  
  
 Türetilmiş bir tür kitaplığından meta verileri kullanarak, çalışma zamanı çağrılan COM nesnesi ve bu nesne için bir sarmalayıcı oluşturur. Her RCW sarmalar ve RCW artık gerekli olmadığında, başvuru COM nesnesi üzerinde serbest COM nesnesindeki arabirim işaretçileri, bir önbelleğini korur. Çalışma Zamanı Modülü çöp toplama RCW üzerinde gerçekleştirir.  
  
 Diğer etkinlikler arasında veri Sarmalanan nesne adına yönetilen ve yönetilmeyen kodu arasında RCW sıralar. Özellikle, istemci ve sunucu arasında aktarılan veriler farklı sunumu sahip olduklarında yöntem bağımsız değişkenleri ve yöntemi dönüş değerleri için hazırlama RCW sağlar.  
  
 Standart sarmalayıcı yerleşik hazırlama kurallarının uygulanmasını sağlar. Örneğin, bir .NET istemci yönetilmeyen nesneye bağımsız değişken bir parçası olarak bir dize türü geçtiğinde, sarmalayıcı dize BSTR türüne dönüştürür. COM nesnesi BSTR yönetilen çağırıcısına döndürmelidir, çağıran bir dize alır. İstemci ve sunucu gönderebilir ve bunlara alışkın olduğu veri alabilirsiniz. Diğer türleri dönüştürme gerektirir. Örneğin, standart bir sarmalayıcı tür dönüştürme olmadan yönetilen ve yönetilmeyen kodu arasında her zaman bir 4-bayt tamsayı geçer.  
  
## <a name="marshaling-selected-interfaces"></a>Seçili arabirimleri hazırlama  
 Birincil amacı, [çalışma zamanı aranabilir sarmalayıcısı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) olan yönetilen ve yönetilmeyen programlama modelleri arasındaki farklar gizlemek için. Sorunsuz bir geçiş oluşturmak için RCW Seçili COM arabirimleri .NET istemciye sokmadan aşağıdaki çizimde gösterildiği gibi kullanır.  
  
 ![RCW ile arabirimleri](../../../docs/framework/interop/media/rcwwithinterfaces.gif "rcwwithinterfaces")  
COM arabirimleri ve çalışma zamanı aranabilir sarmalayıcısı  
  
 Erken bağlama nesnesi olarak oluşturduğunuzda, RCW belirli bir türüdür. COM nesnesi uygular ve yöntemleri, özellikleri ve olayları nesnenin arabirimlerinden gösterir arabirimlerini uygular. Çizimde, RCW INew arabirimi gösterir ancak tüketir **IUnknown** ve **IDispatch** arabirimleri. Ayrıca, RCW .NET istemci INew arabirimin tüm üyeleri ortaya koyar.  
  
 RCW sarmaladığı nesnesi tarafından sunulan aşağıdaki tabloda listelenen arabirimler tüketir.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|**IDispatch**|COM nesnelerine yansıma aracılığıyla geç bağlama için.|  
|**IErrorInfo**|Hata, kaynağı, bir Yardım dosyası, Yardım içeriği ve hata tanımlı arabirimi GUID metinsel açıklaması sağlar (her zaman **GUID_NULL** .NET sınıfları için).|  
|**IProvideClassInfo**|COM Nesne Implements sarılan varsa **IProvideClassInfo'yu**, RCW türü bilgileri daha iyi türü kimlik sağlamak için bu arabirimden ayıklar.|  
|**IUnknown**|Nesne kimliği, türü zorlama ve ömür yönetimi için:<br /><br /> -Nesne Kimliği<br />     Çalışma zamanı değeri karşılaştırarak COM nesneleri arasında ayırt **IUnknown** her nesne için arabirim.<br />-Type zorlama<br />     RCW tarafından gerçekleştirilen dinamik tür bulma tanıdığı **QueryInterface** yöntemi.<br />-Ömür Yönetimi<br />     Kullanarak **QueryInterface** yöntemi RCW alır ve Çalışma Zamanı Modülü çöp toplama yönetilmeyen nesne serbest sarmalayıcı üzerinde gerçekleştirir kadar yönetilmeyen bir nesneye başvuru tutar.|  
  
 RCW isteğe bağlı olarak aşağıdaki tabloda listelenen arabirimler sarmaladığı nesnesi tarafından sunulan tüketir.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|**IConnectionPoint** ve **IConnectionPointContainer**|Bağlantı noktası olayı stili olayları temsilci göre kullanıma RCW dönüştürür nesneleri.|  
|**IDispatchEx**|Sınıf uyguluyorsa **Idispatchex**, RCW uygulayan **IExpando**. **Idispatchex** arabirimi uzantısıdır **IDispatch** aksine, arabirim **IDispatch**, numaralandırma, ekleme, silme, sağlar ve büyük küçük harfe duyarlı üyeleri çağrılıyor.|  
|**IEnumVARIANT**|Koleksiyon olarak kabul edilmesi için numaralandırmalar destekleyen COM türler sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM Sarmalayıcıları](../../../docs/framework/interop/com-wrappers.md)  
 [Seçili arabirimleri hazırlama](http://msdn.microsoft.com/library/fdb97fd0-f694-4832-bf15-a4e7cf413840)  
 [COM Çağrılabilir Sarmalayıcısı](../../../docs/framework/interop/com-callable-wrapper.md)  
 [Derleme dönüştürme özeti için tür kitaplığı](http://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
