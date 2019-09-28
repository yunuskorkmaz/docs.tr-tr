---
title: XML Serileştiricisi Oluşturma Aracı (Sgen.exe)
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: 492337973f71b10dc061353b7083f596b402ae29
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392714"
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
|**/a @ no__t-1ssembly @ no__t-2:** _dosya adı_|*Dosya adı*tarafından belirtilen derlemede veya yürütülebilir dosyada bulunan tüm türler için serileştirme kodu oluşturur. Yalnızca bir dosya adı sağlanabilir. Bu bağımsız değişken yinelenir, son dosya adı kullanılır.|  
|**/c @ no__t-1ompiler @ no__t-2:** _Seçenekler_|C# Derleyici geçirilecek seçeneklerini belirtir. Tüm csc.exe seçenekleri için derleyici geçirilen desteklenir. Bu derleme imzalanması gerektiğini belirtmek ve anahtar dosyasını belirtmek için kullanılabilir.|  
|**/d @ no__t-1ebug @ no__t-2**|Bir hata ayıklayıcısı ile kullanılan bir görüntü oluşturur.|  
|**/f @ no__t-1orce @ no__t-2**|Aynı ada sahip bir varolan derlemenin üzerine zorlar. Varsayılan değer **false**'dur.|  
|**/Help veya/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/k @ no__t-1eep @ no__t-2**|Serileştirme derlemeye derlenen sonra oluşturulan kaynak dosyaların ve diğer geçici dosyaları silmeyi göstermez. Bu araç belirli bir tür için serileştirme kod oluşturmak olup olmadığını belirlemek için kullanılabilir.|  
|**/n @ no__t-1ologo @ no__t-2**|Microsoft başlangıç başlığı görüntülenmesini engeller.|  
|**/o @ no__t-1ut @ no__t-2:** _yol_|Oluşturulan derleme kaydedileceği dizini belirtir. **Not:**  Oluşturulan derleme adı giriş derleme artı "xmlSerializers.dll" adını oluşur.|  
|**/p @ no__t-1roxytypes @ no__t-2**|XML Web hizmeti proxy türleri için yalnızca serileştirme kod oluşturur.|  
|**/r @ no__t-1eference @ no__t-2:** _AssemblyFiles_|XML serileştirme gerektiren türleri tarafından başvurulan bir derleme belirtir. Virgülle ayrılmış birden çok derleme dosyaları kabul eder.|  
|**/s @ no__t-1ilent @ no__t-2**|Başarı iletilerinin görüntülenmesini bastırır.|  
|**/t @ no__t-1türü @ no__t-2:** _tür_|Belirtilen tür için yalnızca serileştirme kod oluşturur.|  
|**/v @ no__t-1erboo @ no__t-2**|Hata ayıklama için ayrıntılı çıktı görüntüler. Listeler ile seri hale getirilemiyor hedef derleme türlerinden <xref:System.Xml.Serialization.XmlSerializer>.|  
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
