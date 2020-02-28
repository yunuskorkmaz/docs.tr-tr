---
title: XML Serileştiricisi Oluşturma Aracı (Sgen.exe)
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: d67ab634279c4f8e06d609950932e2422bc43395
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159526"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>XML Serileştiricisi Oluşturma Aracı (Sgen.exe)
XML seri hale getirici oluşturucunun bir XML serileştirme derleme türleri için başlangıç performansını artırmak için belirtilen derlemesinde oluşturur bir <xref:System.Xml.Serialization.XmlSerializer> zaman serileştiren veya belirtilen türden nesneler seri durumdan çıkarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
sgen [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/a\[erleme\]:** _filename_|*Dosya adı*tarafından belirtilen derlemede veya yürütülebilir dosyada bulunan tüm türler için serileştirme kodu oluşturur. Yalnızca bir dosya adı sağlanabilir. Bu bağımsız değişken yinelenir, son dosya adı kullanılır.|  
|**/c\[ompiler\]:** _Seçenekler_|C# Derleyici geçirilecek seçeneklerini belirtir. Tüm csc.exe seçenekleri için derleyici geçirilen desteklenir. Bu derleme imzalanması gerektiğini belirtmek ve anahtar dosyasını belirtmek için kullanılabilir.|  
|**/d\[ebug\]**|Bir hata ayıklayıcısı ile kullanılan bir görüntü oluşturur.|  
|**/f\[Orce\]**|Aynı ada sahip bir varolan derlemenin üzerine zorlar. Varsayılan değer **false**'dur.|  
|**/Help veya/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/k\[UT\]**|Serileştirme derlemeye derlenen sonra oluşturulan kaynak dosyaların ve diğer geçici dosyaları silmeyi göstermez. Bu araç belirli bir tür için serileştirme kod oluşturmak olup olmadığını belirlemek için kullanılabilir.|  
|**/n\[ologo\]**|Microsoft başlangıç başlığı görüntülenmesini engeller.|  
|**/o\[ut\]:** _yol_|Oluşturulan derleme kaydedileceği dizini belirtir. **Note:**  Oluşturulan derlemenin adı, giriş derlemesinin adından oluşur ve "Xmlserileştiriciler. dll".|  
|**/p\[roxytypes\]**|XML Web hizmeti proxy türleri için yalnızca serileştirme kod oluşturur.|  
|**/r\[eference\]:** _AssemblyFiles_|XML serileştirme gerektiren türleri tarafından başvurulan bir derleme belirtir. Virgülle ayrılmış birden çok derleme dosyaları kabul eder.|  
|**/s\[ilent\]**|Başarı iletilerinin görüntülenmesini bastırır.|  
|**/t\[türü\]:** _tür_|Belirtilen tür için yalnızca serileştirme kod oluşturur.|  
|**/v\[erboo\]**|Hata ayıklama için ayrıntılı çıktı görüntüler. Listeler ile seri hale getirilemiyor hedef derleme türlerinden <xref:System.Xml.Serialization.XmlSerializer>.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 XML seri hale getirici oluşturucunun kullanılmadığında bir <xref:System.Xml.Serialization.XmlSerializer> seri hale getirme kodu ve bir seri hale getirme derlemesi her türü için bir uygulama her çalıştırıldığında oluşturur. XML serileştirme başlatmasının performansını artırmak için SGen. exe aracını kullanarak bu derlemeleri önceden oluşturun. Bu derlemeleri uygulama ile sonra dağıtılabilir.  
  
 XML seri hale getirici oluşturucunun ayrıca seri hale getirme işlemi türü ilk kez yüklendiğinde isabet bir performans tabi olmayan çünkü sunucularla iletişim kurmak için XML Web hizmeti proxy kullanan istemciler performansını geliştirebilir.  
  
 Bu oluşturulan derlemeler bir Web hizmeti sunucu tarafında kullanılamaz. Bu, yalnızca Web hizmeti istemcileri ve el ile serileştirme senaryolar için aracıdır.  
  
 Serileştirilecek tür içeren derlemenin MyType.dll adlandırılmışsa, ardından ilişkili seri hale getirme derlemesi MyType.XmlSerializers.dll olarak adlandırılır.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komutu Data.dll adlı derlemesinde bulunan tüm türleri serileştirmek için Data.XmlSerializers.dll adlı bir derleme oluşturur.  
  
```console  
sgen Data.dll
```  
  
 Seri hale getirmek ve Data.dll türlerinde seri durumdan çıkarılacağı kodundan Data.XmlSerializers.dll derleme başvurulabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](../../../docs/framework/tools/index.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
