---
title: XML Serileştiricisi Oluşturma Aracı (Sgen.exe)
description: XML serileştirici Oluşturucusu, bir derlemedeki türler için bir XML serileştirme derlemesi oluşturur ve bu da XmlSerializer 'ın başlangıç performansını geliştirir.
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: 259f4cbafbe76d3645940ad425f41afb0b8cd304
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653822"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>XML Serileştiricisi Oluşturma Aracı (Sgen.exe)

XML seri hale getirici Oluşturucusu, belirtilen derlemedeki türler için bir XML serileştirme derlemesi oluşturuyor. Serileştirme derlemesi, <xref:System.Xml.Serialization.XmlSerializer> belirtilen türlerin nesnelerini seri hale getirse veya seri hale getirtiğinde bir öğesinin başlangıç performansını geliştirir.
  
## <a name="syntax"></a>Syntax

Aracı komut satırından çalıştırın.
  
```console  
sgen [options]  
```
  
> [!TIP]
> .NET Framework araçlarının düzgün çalışması için, [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell) 'i kullanmanız ya da `Path` ,, `Include` ve `Lib` ortam değişkenlerini doğru şekilde ayarlamanız gerekir. Bu ortam değişkenlerini ayarlamak için, *\<SDK> \\ \<version> \Bin* dizininde bulunan *SDKVars.bat* çalıştırın.
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/a \[ erleme \] :**_dosya adı_|*Dosya adı* tarafından belirtilen derlemede veya yürütülebilir dosyada bulunan tüm türler için serileştirme kodu oluşturur. Yalnızca bir dosya adı sağlanabilir. Bu bağımsız değişken yinelenir, son dosya adı kullanılır.|  
|**/c \[ ompiler \] :**_Seçenekler_|C# Derleyici geçirilecek seçeneklerini belirtir. Tüm csc.exe seçenekleri için derleyici geçirilen desteklenir. Bu derleme imzalanması gerektiğini belirtmek ve anahtar dosyasını belirtmek için kullanılabilir.|  
|**/d \[ ebug\]**|Bir hata ayıklayıcısı ile kullanılan bir görüntü oluşturur.|  
|**/f \[ Orce\]**|Aynı ada sahip bir varolan derlemenin üzerine zorlar. Varsayılan değer **false**'dur.|  
|**/Help veya/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/k \[ UT\]**|Serileştirme derlemeye derlenen sonra oluşturulan kaynak dosyaların ve diğer geçici dosyaları silmeyi göstermez. Bu araç belirli bir tür için serileştirme kod oluşturmak olup olmadığını belirlemek için kullanılabilir.|  
|**/n \[ ologo\]**|Microsoft başlangıç başlığı görüntülenmesini engeller.|  
|**/o \[ UT \] :**_yol_|Oluşturulan derleme kaydedileceği dizini belirtir. **Note:**  Oluşturulan derlemenin adı, giriş derlemesinin adından ve "xmlSerializers.dll" oluşur.|  
|**/p \[ roxytypes\]**|XML Web hizmeti proxy türleri için yalnızca serileştirme kod oluşturur.|  
|**/r \[ eference \] :**_AssemblyFiles_|XML serileştirme gerektiren türleri tarafından başvurulan bir derleme belirtir. Virgülle ayrılmış birden çok derleme dosyaları kabul eder.|  
|**/s \[ ilent\]**|Başarı iletilerinin görüntülenmesini bastırır.|  
|**/t \[ türü \] :**_tür_|Belirtilen tür için yalnızca serileştirme kod oluşturur.|  
|**/v \[ erboo\]**|Hata ayıklama için ayrıntılı çıktı görüntüler. Listeler ile seri hale getirilemiyor hedef derleme türlerinden <xref:System.Xml.Serialization.XmlSerializer>.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  

 XML seri hale getirici oluşturucunun kullanılmadığında bir <xref:System.Xml.Serialization.XmlSerializer> seri hale getirme kodu ve bir seri hale getirme derlemesi her türü için bir uygulama her çalıştırıldığında oluşturur. XML serileştirme başlatmasının performansını artırmak için, bu derlemeleri önceden oluşturmak üzere Sgen.exe aracını kullanın. Bu derlemeleri uygulama ile sonra dağıtılabilir.  
  
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

- [Araçlar](../../framework/tools/index.md)
- [Geliştirici komut satırı kabukları](/visualstudio/ide/reference/command-prompt-powershell)
