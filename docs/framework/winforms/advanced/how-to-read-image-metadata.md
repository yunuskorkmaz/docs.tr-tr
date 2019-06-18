---
title: 'Nasıl yapılır: Görüntü Meta Verilerini Okuma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 3266724503960b8b45cd134dfa5b007a58d578fa
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169807"
---
# <a name="how-to-read-image-metadata"></a>Nasıl yapılır: Görüntü Meta Verilerini Okuma
Bazı görüntü dosyaları, görüntü özelliklerini belirlemek için okuyabilecekleri meta veriler içerir. Örneğin, dijital hello'nun marka ve model görüntü yakalamak için kullanılan kameranın belirlemek için okuyabilecekleri bir meta veri içerebilir. İle [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], var olan meta verileri okuyabilir ve görüntü dosyaları ayrıca yeni meta veriler yazabilirsiniz.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] meta verilerde tek bir parçası olarak depolayan bir <xref:System.Drawing.Imaging.PropertyItem> nesne. Okuyabilirsiniz <xref:System.Drawing.Image.PropertyItems%2A> özelliği bir <xref:System.Drawing.Image> bir dosyanın tüm meta verileri alınacak nesne. <xref:System.Drawing.Image.PropertyItems%2A> Özelliği, bir dizi döndürür <xref:System.Drawing.Imaging.PropertyItem> nesneleri.  
  
 A <xref:System.Drawing.Imaging.PropertyItem> nesne aşağıdaki dört özelliklere sahiptir: `Id`, `Value`, `Len`, ve `Type`.  
  
## <a name="id"></a>Id  
 Meta veri öğesini tanımlayan etiket. Atanabilir bazı değerler <xref:System.Drawing.Imaging.PropertyItem.Id%2A> aşağıdaki tabloda gösterilmiştir.  
  
|Onaltılık değer|Açıklama|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Resmin başlığı<br /><br /> Donanım üreticisi<br /><br /> Donanım modeli<br /><br /> ExifDTOriginal<br /><br /> EXIF tehditlere maruz kalabileceği süreyi<br /><br /> Aydınlatma tablo<br /><br /> Chrominance tablo|  
  
## <a name="value"></a>Değer  
 Değerleri dizisi. Değerlerin biçimini tarafından belirlenen <xref:System.Drawing.Imaging.PropertyItem.Type%2A> özelliği.  
  
## <a name="len"></a>Len  
 Değerler dizisi uzunluğu (bayt cinsinden) tarafından işaret edilen <xref:System.Drawing.Imaging.PropertyItem.Value%2A> özelliği.  
  
## <a name="type"></a>Tür  
 Dizideki değerleri veri türü tarafından işaret edilen `Value` özelliği. Tarafından belirtilen biçimleri `Type` özellik değerleri aşağıdaki tabloda gösterilen  
  
|Sayısal değer|Açıklama|  
|-------------------|-----------------|  
|1\.|A `Byte`|  
|2|Bir dizi `Byte` ASCII kodlamalı nesneler|  
|3|Bir 16 bit tam sayı|  
|4|Bir 32 bit tamsayı|  
|5|İki `Byte` rasyonel sayı temsil eden nesneleri|  
|6|Kullanılan değil|  
|7|Tanımlanmadı|  
|8|Kullanılan değil|  
|9|`SLong`|  
|10|`SRational`|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki kod örneği okur ve dosyadaki meta verileri yedi parçalarını görüntüler `FakePhoto.jpg`. Listedeki ikinci (dizin 1) özelliği öğeye sahip <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (ekipman üreticisi) ve <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII kodlamalı bayt dizisi). Kod örneği, bu özellik öğesinin değeri görüntüler.  
  
 Kodu aşağıdakine benzer bir çıktı üretir:  
 
```
 Property Item 0
  
 id: 0x320
  
 type: 2
 
 length: 16 bytes 
  
 Property Item 1
  
 id: 0x10f
  
 type: 2 
  
 length: 17 bytes
  
 Property Item 2
  
 id: 0x110
  
 type: 2
  
 length: 7 bytes
  
 Property Item 3
  
 id: 0x9003
  
 type: 2
  
 length: 20 bytes
  
 Property Item 4
  
 id: 0x829a
  
 type: 5
  
 length: 8 bytes
  
 Property Item 5
  
 id: 0x5090
  
 type: 3
  
 length: 128 bytes
  
 Property Item 6
  
 id: 0x5091
  
 type: 3
  
 length: 128 bytes
  
 The equipment make is Northwind Camera.
 ```
  
### <a name="code"></a>Kod  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Formun işlemek <xref:System.Windows.Forms.Control.Paint> olay ve bu kodu Boya olay işleyicisine yapıştırın. Değiştirmeniz gereken `FakePhoto.jpg` bir görüntü adı ve yolu içeri aktarma ve sistem geçerli `System.Drawing.Imaging` ad alanı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
