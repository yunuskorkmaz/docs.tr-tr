---
title: WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Yöntemi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
api_name:
- System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream
api_location:
- System.Runtime.WindowsRuntime.dll
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16f878abc11589fe62f78d941b367d82d7b49e1c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32768521"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a>WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Yöntemi
[.NET Framework 4.5.1 ve sonraki sürümlerinde desteklenen]  
  
 Belirtilen akışı rasgele erişim akışına dönüştürür.  
  
 **Namespace:** <xref:System.IO?displayProperty=nameWithType>  
 **Derleme:** System.Runtime.WindowsRuntime (içinde System.Runtime.WindowsRuntime.dll)  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp  
[CLSCompliantAttribute(false)]  
public static  IRandomAccessStream AsRandomAccessStream(Stream stream)  
```  
  
```vb  
'Declaration  
<ExtensionAttribute> _  
<CLSCompliantAttribute(False)> _  
Public Shared Function AsRandomAccessStream ( _  
        stream As Stream) As IRandomAccessStream  
```  
  
#### <a name="parameters"></a>Parametreler  
 `stream`  
  
 Türü: <xref:System.IO.Stream?displayProperty=nameWithType>  
Dönüştürülecek akış.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Tür: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)  
A [!INCLUDE[wrt](../../../includes/wrt-md.md)] dönüştürülen akışı temsil eden rasgele erişim akış.  
  
## <a name="exceptions"></a>Özel Durumlar  
  
|Özel Durum|Koşul|  
|---------------|---------------|  
|<xref:System.NotSupportedException>|Dönüştürülecek akış, aramayı desteklemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu genişletme yöntemi yalnızca Windows Mağazası uygulamaları geliştirirken kullanılabilir. Bu yöntem Windows Mağazası uygulamalarında akışlarla çalışmak için uygun bir yol sağlar. Dönüştürmek istediğiniz .NET Framework Akış aramayı desteklemelidir. Daha fazla bilgi için bkz: <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> yöntemi.  
  
> [!IMPORTANT]
>  Bu API, .NET Framework 4.5.1 ve sonraki sürümlerinde, ancak sürüm 4.5 desteklenir.  
  
## <a name="version-information"></a>Sürüm Bilgileri  
 **Windows mağazası uygulamaları için .NET**  
  
 Desteklendiği sürüm: Windows 8.1  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions`  
 [Nasıl yapılır: .NET Framework Akışları ile Windows Çalışma Zamanı Akışları Arasında Dönüştürme](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
