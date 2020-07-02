---
title: 'Nasıl Yapılır: JPEG Sıkıştırma Düzeyini Ayarlama'
description: Windows Forms sıkıştırma düzeyini değiştirerek bir JPEG görüntüsünün kalitesini ayarlamayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], changing encoder parameters
- JPEG images [Windows Forms], setting quality level
ms.assetid: 4b9a74e3-9504-43c1-9f28-ace651d0772e
ms.openlocfilehash: 1f6a96e8a05fff40eb08da0ce318faa86a06cc3a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618720"
---
# <a name="how-to-set-jpeg-compression-level"></a>Nasıl Yapılır: JPEG Sıkıştırma Düzeyini Ayarlama
Dosya boyutunu en aza indirmek veya kalitesini artırmak için görüntüyü diske kaydettiğinizde görüntünün parametrelerini değiştirmek isteyebilirsiniz. Bir JPEG görüntüsünün kalitesini, sıkıştırma düzeyini değiştirerek ayarlayabilirsiniz. Bir JPEG görüntüsünü kaydettiğinizde sıkıştırma düzeyini belirtmek için bir <xref:System.Drawing.Imaging.EncoderParameters> nesnesi oluşturmanız ve bunu <xref:System.Drawing.Image.Save%2A> sınıfının yöntemine geçirmeniz gerekir <xref:System.Drawing.Image> . <xref:System.Drawing.Imaging.EncoderParameters>Nesnesinden oluşan bir diziye sahip olacak şekilde nesneyi başlatın <xref:System.Drawing.Imaging.EncoderParameter> . Oluştururken, <xref:System.Drawing.Imaging.EncoderParameter> <xref:System.Drawing.Imaging.Encoder.Quality> kodlayıcıyı ve istenen sıkıştırma düzeyini belirtin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod, bir <xref:System.Drawing.Imaging.EncoderParameter> nesnesi oluşturur ve üç JPEG görüntüsünü kaydeder. Her JPEG görüntüsü, oluşturucuya geçirilen değeri değiştirerek farklı bir kalite düzeyiyle kaydedilir `long` <xref:System.Drawing.Imaging.EncoderParameter> . 0 kalite düzeyi en büyük sıkıştırmaya karşılık gelir ve 100 kalite düzeyi en az sıkıştırmaya karşılık gelir.  
  
```csharp  
private void VaryQualityLevel()  
    {  
        // Get a bitmap. The using statement ensures objects  
        // are automatically disposed from memory after use.  
        using (Bitmap bmp1 = new Bitmap(@"C:\TestPhoto.jpg"))  
        {  
            ImageCodecInfo jpgEncoder = GetEncoder(ImageFormat.Jpeg);  
  
            // Create an Encoder object based on the GUID  
            // for the Quality parameter category.  
            System.Drawing.Imaging.Encoder myEncoder =  
                System.Drawing.Imaging.Encoder.Quality;  
  
            // Create an EncoderParameters object.  
            // An EncoderParameters object has an array of EncoderParameter  
            // objects. In this case, there is only one  
            // EncoderParameter object in the array.  
            EncoderParameters myEncoderParameters = new EncoderParameters(1);  
  
            EncoderParameter myEncoderParameter = new EncoderParameter(myEncoder, 50L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"c:\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters);  
  
            myEncoderParameter = new EncoderParameter(myEncoder, 100L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters);  
  
            // Save the bitmap as a JPG file with zero quality level compression.  
            myEncoderParameter = new EncoderParameter(myEncoder, 0L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters);  
        }  
    }  
```  
  
```vb  
Private Sub VaryQualityLevel()  
    ' Get a bitmap. The Using statement ensures objects  
    ' are automatically disposed from memory after use.  
    Using bmp1 As New Bitmap("C:\test\TestPhoto.jpg")  
        Dim jpgEncoder As ImageCodecInfo = GetEncoder(ImageFormat.Jpeg)  
  
        ' Create an Encoder object based on the GUID  
        ' for the Quality parameter category.  
        Dim myEncoder As System.Drawing.Imaging.Encoder = System.Drawing.Imaging.Encoder.Quality  
  
        ' Create an EncoderParameters object.  
        ' An EncoderParameters object has an array of EncoderParameter  
        ' objects. In this case, there is only one  
        ' EncoderParameter object in the array.  
        Dim myEncoderParameters As New EncoderParameters(1)  
  
        Dim myEncoderParameter As New EncoderParameter(myEncoder, 50L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("c:\test\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters)  
  
        myEncoderParameter = New EncoderParameter(myEncoder, 100L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters)  
  
        ' Save the bitmap as a JPG file with zero quality level compression.  
        myEncoderParameter = New EncoderParameter(myEncoder, 0L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters)  
    End Using  
End Sub  
```  
  
```csharp  
private ImageCodecInfo GetEncoder(ImageFormat format)  
{  
    ImageCodecInfo[] codecs = ImageCodecInfo.GetImageDecoders();  
    foreach (ImageCodecInfo codec in codecs)  
    {  
        if (codec.FormatID == format.Guid)  
        {  
            return codec;  
        }  
    }  
    return null;  
}  
```  
  
```vb  
Private Function GetEncoder(ByVal format As ImageFormat) As ImageCodecInfo  
  
    Dim codecs As ImageCodecInfo() = ImageCodecInfo.GetImageDecoders()  
    Dim codec As ImageCodecInfo  
    For Each codec In codecs  
        If codec.FormatID = format.Guid Then  
            Return codec  
        End If  
    Next codec  
    Return Nothing  
  
End Function  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- Bir Windows Forms uygulaması.  
  
- Parametresi olan bir <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.PaintEventHandler> .  
  
- Adlandırılmış `TestPhoto.jpg` ve **c \\ :** konumunda bulunan bir görüntü dosyası.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Bir Kodlayıcı Tarafından Desteklenen Parametreleri Belirleme](how-to-determine-the-parameters-supported-by-an-encoder.md)
- [Bit Eşlem Türleri](types-of-bitmaps.md)
- [Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma](using-image-encoders-and-decoders-in-managed-gdi.md)
