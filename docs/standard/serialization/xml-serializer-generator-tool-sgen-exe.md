---
title: XML seri hale getirici Oluşturma Aracı (Sgen.exe)
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: 54afa99af3365c3be8a9662905467fbcaf4e8aa3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589185"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>XML seri hale getirici Oluşturma Aracı (Sgen.exe)
XML seri hale getirici oluşturucunun bir XML serileştirme derleme türleri için başlangıç performansını artırmak için belirtilen derlemesinde oluşturur bir <xref:System.Xml.Serialization.XmlSerializer> zaman serileştiren veya belirtilen türden nesneler seri durumdan çıkarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
sgen [options]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/a**[**ssembly**] **: *** filename*|Tüm derlemesinde bulunan türleri veya tarafından belirtilen yürütülebilir dosya için seri hale getirme kod oluşturur *filename*. Yalnızca bir dosya adı sağlanabilir. Bu bağımsız değişken yinelenir, son dosya adı kullanılır.|  
|**/c [ompiler]:** *seçenekleri*|C# Derleyici geçirilecek seçeneklerini belirtir. Tüm csc.exe seçenekleri için derleyici geçirilen desteklenir. Bu derleme imzalanması gerektiğini belirtmek ve anahtar dosyasını belirtmek için kullanılabilir.|  
|**/d**[**ebug**]|Bir hata ayıklayıcısı ile kullanılan bir görüntü oluşturur.|  
|**/f [orce]**|Aynı ada sahip bir varolan derlemenin üzerine zorlar. Varsayılan değer **false**.|  
|**/ help veya /?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/ k**[**almayı durumunu Sürdür**]|Serileştirme derlemeye derlenen sonra oluşturulan kaynak dosyaların ve diğer geçici dosyaları silmeyi göstermez. Bu araç belirli bir tür için serileştirme kod oluşturmak olup olmadığını belirlemek için kullanılabilir.|  
|**/n**[**ologo**]|Microsoft başlangıç başlığı görüntülenmesini engeller.|  
|**/o**[**ut**] **: *** yolu*|Oluşturulan derleme kaydedileceği dizini belirtir. **Not:** oluşturulan derleme adını giriş derleme artı "xmlSerializers.dll" adından oluşur.|  
|**/p**[**roxytypes**]|XML Web hizmeti proxy türleri için yalnızca serileştirme kod oluşturur.|  
|**/r**[**vuru**] **: *** assemblyfiles*|XML serileştirme gerektiren türleri tarafından başvurulan bir derleme belirtir. Virgülle ayrılmış birden çok derleme dosyaları kabul eder.|  
|**/s**[**ilent**]|Başarı iletilerinin görüntülenmesini bastırır.|  
|**/t**[**türü**] **: *** türü*|Belirtilen tür için yalnızca serileştirme kod oluşturur.|  
|**/v**[**erbose**]|Hata ayıklama için ayrıntılı çıktı görüntüler. Listeler ile seri hale getirilemiyor hedef derleme türlerinden <xref:System.Xml.Serialization.XmlSerializer>.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 XML seri hale getirici oluşturucunun kullanılmadığında bir <xref:System.Xml.Serialization.XmlSerializer> seri hale getirme kodu ve bir seri hale getirme derlemesi her türü için bir uygulama her çalıştırıldığında oluşturur. XML serileştirme başlangıç performansını artırmak için bu derlemeler önceden oluşturmak üzere Sgen.exe aracını kullanın. Bu derlemeleri uygulama ile sonra dağıtılabilir.  
  
 XML seri hale getirici oluşturucunun ayrıca seri hale getirme işlemi türü ilk kez yüklendiğinde isabet bir performans tabi olmayan çünkü sunucularla iletişim kurmak için XML Web hizmeti proxy kullanan istemciler performansını geliştirebilir.  
  
 Bu oluşturulan derlemeler bir Web hizmeti sunucu tarafında kullanılamaz. Bu, yalnızca Web hizmeti istemcileri ve el ile serileştirme senaryolar için aracıdır.  
  
 Serileştirilecek tür içeren derlemenin MyType.dll adlandırılmışsa, ardından ilişkili seri hale getirme derlemesi MyType.XmlSerializers.dll olarak adlandırılır.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komutu Data.dll adlı derlemesinde bulunan tüm türleri serileştirmek için Data.XmlSerializers.dll adlı bir derleme oluşturur.  
  
```  
sgen Data.dll   
```  
  
 Seri hale getirmek ve Data.dll türlerinde seri durumdan çıkarılacağı kodundan Data.XmlSerializers.dll derleme başvurulabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [XML Web Hizmetleri genel bakış](https://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
