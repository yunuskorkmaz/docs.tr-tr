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
# <a name="how-to-set-jpeg-compression-level"></a><span data-ttu-id="f8380-103">Nasıl Yapılır: JPEG Sıkıştırma Düzeyini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="f8380-103">How to: Set JPEG Compression Level</span></span>
<span data-ttu-id="f8380-104">Dosya boyutunu en aza indirmek veya kalitesini artırmak için görüntüyü diske kaydettiğinizde görüntünün parametrelerini değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8380-104">You may want to modify the parameters of an image when you save the image to disk to minimize the file size or improve its quality.</span></span> <span data-ttu-id="f8380-105">Bir JPEG görüntüsünün kalitesini, sıkıştırma düzeyini değiştirerek ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8380-105">You can adjust the quality of a JPEG image by modifying its compression level.</span></span> <span data-ttu-id="f8380-106">Bir JPEG görüntüsünü kaydettiğinizde sıkıştırma düzeyini belirtmek için bir <xref:System.Drawing.Imaging.EncoderParameters> nesnesi oluşturmanız ve bunu <xref:System.Drawing.Image.Save%2A> sınıfının yöntemine geçirmeniz gerekir <xref:System.Drawing.Image> .</span><span class="sxs-lookup"><span data-stu-id="f8380-106">To specify the compression level when you save a JPEG image, you must create an <xref:System.Drawing.Imaging.EncoderParameters> object and pass it to the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="f8380-107"><xref:System.Drawing.Imaging.EncoderParameters>Nesnesinden oluşan bir diziye sahip olacak şekilde nesneyi başlatın <xref:System.Drawing.Imaging.EncoderParameter> .</span><span class="sxs-lookup"><span data-stu-id="f8380-107">Initialize the <xref:System.Drawing.Imaging.EncoderParameters> object so that it has an array that consists of one <xref:System.Drawing.Imaging.EncoderParameter>.</span></span> <span data-ttu-id="f8380-108">Oluştururken, <xref:System.Drawing.Imaging.EncoderParameter> <xref:System.Drawing.Imaging.Encoder.Quality> kodlayıcıyı ve istenen sıkıştırma düzeyini belirtin.</span><span class="sxs-lookup"><span data-stu-id="f8380-108">When you create the <xref:System.Drawing.Imaging.EncoderParameter>, specify the <xref:System.Drawing.Imaging.Encoder.Quality> encoder, and the desired compression level.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8380-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8380-109">Example</span></span>  
 <span data-ttu-id="f8380-110">Aşağıdaki örnek kod, bir <xref:System.Drawing.Imaging.EncoderParameter> nesnesi oluşturur ve üç JPEG görüntüsünü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f8380-110">The following example code creates an <xref:System.Drawing.Imaging.EncoderParameter> object and saves three JPEG images.</span></span> <span data-ttu-id="f8380-111">Her JPEG görüntüsü, oluşturucuya geçirilen değeri değiştirerek farklı bir kalite düzeyiyle kaydedilir `long` <xref:System.Drawing.Imaging.EncoderParameter> .</span><span class="sxs-lookup"><span data-stu-id="f8380-111">Each JPEG image is saved with a different quality level, by modifying the `long` value passed to the <xref:System.Drawing.Imaging.EncoderParameter> constructor.</span></span> <span data-ttu-id="f8380-112">0 kalite düzeyi en büyük sıkıştırmaya karşılık gelir ve 100 kalite düzeyi en az sıkıştırmaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f8380-112">A quality level of 0 corresponds to the greatest compression, and a quality level of 100 corresponds to the least compression.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8380-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f8380-113">Compiling the Code</span></span>  
 <span data-ttu-id="f8380-114">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f8380-114">This example requires:</span></span>  
  
- <span data-ttu-id="f8380-115">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="f8380-115">A Windows Forms application.</span></span>  
  
- <span data-ttu-id="f8380-116">Parametresi olan bir <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.PaintEventHandler> .</span><span class="sxs-lookup"><span data-stu-id="f8380-116">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
- <span data-ttu-id="f8380-117">Adlandırılmış `TestPhoto.jpg` ve **c \\ :** konumunda bulunan bir görüntü dosyası.</span><span class="sxs-lookup"><span data-stu-id="f8380-117">An image file that is named `TestPhoto.jpg` and located at **c:\\**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8380-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8380-118">See also</span></span>

- [<span data-ttu-id="f8380-119">Nasıl yapılır: Bir Kodlayıcı Tarafından Desteklenen Parametreleri Belirleme</span><span class="sxs-lookup"><span data-stu-id="f8380-119">How to: Determine the Parameters Supported by an Encoder</span></span>](how-to-determine-the-parameters-supported-by-an-encoder.md)
- [<span data-ttu-id="f8380-120">Bit Eşlem Türleri</span><span class="sxs-lookup"><span data-stu-id="f8380-120">Types of Bitmaps</span></span>](types-of-bitmaps.md)
- [<span data-ttu-id="f8380-121">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="f8380-121">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
