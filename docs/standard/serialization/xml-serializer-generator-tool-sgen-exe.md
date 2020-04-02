---
title: XML Serileştiricisi Oluşturma Aracı (Sgen.exe)
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: bc1a0abaeef9a9244aa83941e590063c7ef167d1
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588357"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>XML Serileştiricisi Oluşturma Aracı (Sgen.exe)

XML Serializer Generator, belirli bir derlemedeki türleri için bir XML serileştirme derlemesi oluşturur. Serileştirme derlemesi, belirtilen türdeki nesneleri serileştirdiğinde veya deserialize ettiğinde bir <xref:System.Xml.Serialization.XmlSerializer> başlangıç performansını artırır.
  
## <a name="syntax"></a>Sözdizimi

Aracı komut satırından çalıştırın.
  
```console  
sgen [options]  
```
  
> [!TIP]
> .NET Framework araçlarının düzgün çalışması için `Path`, `Include`ve `Lib` çevre değişkenlerinizi doğru ayarlamanız gerekir. \<SDK>\v2.0\Bin dizininde bulunan SDKVars.bat'ı çalıştırarak bu ortam değişkenlerini ayarlayın. Her komut kabuğu'nu SDKVars.bat yürütülmelidir.
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/a\[ssembly\]:**_filename_|Dosya *adı*ile belirtilen derlemede veya yürütülebilir de bulunan tüm türler için serileştirme kodu oluşturur. Yalnızca bir dosya adı sağlanabilir. Bu bağımsız değişken yinelenir, son dosya adı kullanılır.|  
|**/c\[ompiler\]:**_seçenekler_|C# Derleyici geçirilecek seçeneklerini belirtir. Tüm csc.exe seçenekleri için derleyici geçirilen desteklenir. Bu derleme imzalanması gerektiğini belirtmek ve anahtar dosyasını belirtmek için kullanılabilir.|  
|**/d\[ebug\]**|Bir hata ayıklayıcısı ile kullanılan bir görüntü oluşturur.|  
|**/f\[orce\]**|Aynı ada sahip bir varolan derlemenin üzerine zorlar. Varsayılan **yanlıştır.**|  
|**/yardım veya /?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/k\[eep\]**|Serileştirme derlemeye derlenen sonra oluşturulan kaynak dosyaların ve diğer geçici dosyaları silmeyi göstermez. Bu araç belirli bir tür için serileştirme kod oluşturmak olup olmadığını belirlemek için kullanılabilir.|  
|**/n\[ologo\]**|Microsoft başlangıç başlığı görüntülenmesini engeller.|  
|**/o\[\]ut :**_yol_|Oluşturulan derleme kaydedileceği dizini belirtir. **Not:**  Oluşturulan derlemenin adı giriş derlemesinin adı artı "xmlSerializers.dll" adresinden oluşur.|  
|**/p\[roxytypes\]**|XML Web hizmeti proxy türleri için yalnızca serileştirme kod oluşturur.|  
|**/r\[eference\]:**_assemblyfiles_|XML serileştirme gerektiren türleri tarafından başvurulan bir derleme belirtir. Virgülle ayrılmış birden çok derleme dosyaları kabul eder.|  
|**/s\[ilent\]**|Başarı iletilerinin görüntülenmesini bastırır.|  
|**/t\[\]ype :**_yazı_|Belirtilen tür için yalnızca serileştirme kod oluşturur.|  
|**/v\[erbose\]**|Hata ayıklama için ayrıntılı çıktı görüntüler. Listeler ile seri hale getirilemiyor hedef derleme türlerinden <xref:System.Xml.Serialization.XmlSerializer>.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 XML seri hale getirici oluşturucunun kullanılmadığında bir <xref:System.Xml.Serialization.XmlSerializer> seri hale getirme kodu ve bir seri hale getirme derlemesi her türü için bir uygulama her çalıştırıldığında oluşturur. XML serileştirme başlatmanın performansını artırmak için, bu derlemeleri önceden oluşturmak için Sgen.exe aracını kullanın. Bu derlemeleri uygulama ile sonra dağıtılabilir.  
  
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
